## IRQ Numbers

The following list of IRQ numbers specifies what each of the 16 IRQ lines are used for.

| IRQ Number | Typical Use | Description |
| --- | --- | --- |
| IRQ 0 | System timer | This interrupt is reserved for the internal system timer. It is never available to peripherals or other devices. |
| IRQ 1 | Keyboard | This interrupt is reserved for the keyboard controller. Even on devices without a keyboard, this interrupt is exclusively for keyboard input. |
| IRQ 2 | Cascade interrupt for IRQs 8-15 | This interrupt cascades the second interrupt controller to the first. |
| IRQ 3 | Second serial port (COM2) | The interrupt for the second serial port and often the default interrupt for the fourth serial port (COM4). |
| IRQ 4 | First serial port (COM1) | This interrupt is normally used for the first serial port. On devices that do not use a PS/2 mouse, this interrupt is almost always used by the serial mouse. This is also the default interrupt for the third serial port (COM3). |
| IRQ 5 | Sound card | This interrupt is the first choice that most sound cards make when looking for an IRQ setting. |
| IRQ 6 | Floppy disk controller | This interrupt is reserved for the floppy disk controller. |
| IRQ 7 | First parallel port | This interrupt is normally reserved for the use of the printer. If a printer is not being used, this interrupt can be used for other devices that use parallel ports. | 
| IRQ 8 | Real-time clock | This interrupt is reserved for the system's real-time clock timer and can not be used for any other purpose. |
| IRQ 9 | Open interrupt | This interrupt is typically left open on devices for the use of peripherals. |
| IRQ 10 | Open interrupt | This interrupt is typically left open on devices for the use of peripherals. |
| IRQ 11 | Open interrupt | This interrupt is typically left open on devices for the use of peripherals. |
| IRQ 12 | PS/2 mouse | This interrupt is reserved for the PS/2 mouse on machines that use one. If a PS/2 mouse is not used, the interrupt can be used for other peripherals, such as network card. |
| IRQ 13 | Floating point unit/coprocessor | This interrupt is reserved for the integrated floating point unit. It is never available to peripherals or other devices as it is used exclusively for internal signaling. |
| IRQ 14 | Primary IDE channel | This interrupt is reserved for use by the primary IDE controller. On systems that do not use IDE devices, the IRQ can be used for another purpose. |
| IRQ 15 | Secondary IDE channel | This interrupt is reserved for use by the secondary IDE controller. |

## Baud rate :vs: Bit rate

The **bandwidth** of a digital signal is the number of bits transmitted per second. The **baud rate** is the number of signalling elements transmitted per second.

In simple systems each signalling element encodes one bit, so the two values are the same. In more complex systems, the number of bits encoded per signalling element may be greater than one, so the bandwidth will be some multiple of the baud rate.

What’s a signalling element? It’s some physical phenomenon that can be transmitted in a finite time, in some number of different forms. A single cycle of a sine wave is a good example. Let’s say that we transmit a sine wave, and at the start of each cycle, we set the amplitude to 5V or 10V. Then each cycle of the sine wave could be interpreted as meaning 0 or 1 - it would carry one bit of data; the bit rate would be 1mbps, and the baud rate wold be 1 million baud.

However, if we could drive each cycle of the sine wave to any of 4 different amplitudes (5V, 10V, 15V and 20V, say), and distinguish between those voltages at the receiving end of the transmission channel, then we could use each cycle to represent a two-bit value (5V => 00, 10V => 01, 15V => 10, 20V => 11, say). The baud rate (the number of signalling elements per second) would remain unchanged at 1 megabaud, but we’d be getting 2 million bits per second out of the data channel.

If in addition to messing about with the amplitude of the sine wave, we could also manipulate its phase, so that at the start of the cycle time it was shifted by 0 degrees, 90 degrees, 180 degrees or 270 degrees, then we’d have a total of 16 different distinct signalling elements, since each cycle of the sine wave could have any of four different voltages, and each of those amplitudes could be associated with four different phase shifts.

Phase-and-amplitude signalling, often called Quadrature Amplitude Modulation, is a popular way of encoding data in real world signalling systems.

From the description given above, it may seem that you could go on adding amplitudes and phases shifts to a carrier wave and get infinite bandwidth out of any given baud rate. However Claude Shannon invented information theory to tell us that for any given frequency of carrier wave, there is a fixed limit, and his theory is borne out in practice. But that, as they say, is a story for another day.

## Serial Port: Transmit Data and Receive Data

### Transmitting

Transmitting is sending bytes data out of the serial port away from the computer. Once you understand transmitting, receiving is easy to understand since it's similar. The first explanation given here will be grossly oversimplified. Then more detail will be added in later explanations. When the computer wants to send a byte out the serial port (to the external cable) the CPU sends the byte on the bus inside the computer to the I/O address of the serial port. The serial port takes the byte, and sends it out one bit at a time (a serial bit-stream) on the transmit pin of the serial cable connector.

The UART chip done most of the work at the serial port, you can say UART is serial port engine. To transmit a data byte, the serial device driver program sends a data to the serial port I/O address. This data gets into a 1-byte "transmit shift register" in the serial port. From this shift register bits are taken from the data one-by-one byte and sent out bit-by-bit on the serial line. Then when the last bit has been sent and the shift register needs another byte data to send it could just ask confirm the CPU to send it another byte data. Thus would be simple but it would likely introduce delays since the CPU might not be able to get the byte immediately. After all, the CPU is usually doing other things besides just handling the serial port.

A way to eliminate such delays is to arrange things so that the CPU gets the byte data before the shift register needs it and stores it in a serial port hardware buffer. Then when the shift register has sent out its byte data and needs a new byte immediately, the serial port hardware just transfers the next byte from its own buffer to the shift register. No need to call the CPU to fetch a new byte.

The size of this serial port buffer was originally only one byte; today it is usually 16 bytes. Now there is still the problem of keeping this buffer sufficiently supplied with bytes so that when the shift register needs a byte to transmit it will always find one there (unless there are no more bytes to send). CPU using an interrupt does this.

When the shift register grabs the byte out of the buffer and the buffer needs another byte, it sends an interrupt to the CPU by putting a voltage on a dedicated wire on the computer bus. Unless the CPU is doing something very important, the interrupt forces it to stop what it was doing and start running a program which will supply another byte to the port's buffer. The purpose of this buffer is to keep an extra byte (waiting to be sent) queued in hardware so that there will be no gaps in the transmission of bytes out the serial port cable.

Once the CPU gets the interrupt, it will know who sent the interrupt since there is a dedicated interrupt wire for each serial port (unless interrupts are shared).

Then the CPU will start running the serial device driver which checks registers at I/0 addresses to find out what has happened. It finds out that the serial's transmit buffer is empty and waiting for another byte. So if there are more bytes to send, it sends the next byte to the serial port's I/0 address. This next byte should arrive when the previous byte is still in the transmit shift register and is still being transmitted bit-by-bit.

In review, when a byte has been fully transmitted out the transmit wire of the serial port and the shift register is now empty the following 3 things happen almost simultaneously:
1. The next byte is moved from the transmit buffer into the transmit shift register.
2. The transmission of this new byte (bit-by-bit) begins.
3. Another interrupt is issued to tell the device driver to send yet another byte to the now empty transmit buffer.

Thus we say that the serial port is interrupt driven. Each time the serial port issues an interrupt; the CPU sends it another byte. Once a byte has been sent to the transmit buffer by the CPU, then the CPU is free to pursue some other activity until it gets the next interrupt. The serial port transmits bits at a fixed rate, which is selected by the user (or an application program). It's sometimes called the baud rate. The serial port also adds extra bits to each byte (start, stop and perhaps parity bits) so there are often 10 bits sent per byte. At a rate (also called speed) of 19,200 bits per second (bps), there are thus 1,920 bytes/sec (and also 1,920 interrupts/sec).

Doing all this is a lot of work for the CPU. This is true for many reasons. First, just sending one 8-bit byte at a time over a 32-bit data bus (or even 64-bit) is not a very efficient use of bus width. Also, there is a lot of overhead in handing each interrupt. When the interrupt is received, the device driver only knows that something caused an interrupt at the serial port but doesn't know that it's because a character has been sent. The device driver has to make various checks to find out what happened. The same interrupt could mean that a character was received, one of the control lines changed state, etc.

A major improvement has been the enlargement of the buffer size of the serial port from 1-byte to 16-bytes. This means that when the CPU gets an interrupt it gives the serial port up to 16 new bytes to transmit. This is interrupt to service but data must still be transferred one byte at a time over a wide bus. The 16-byte buffer is actually a FIFO (First In First Out) queue and is often called a FIFO. See FIFOs for details about the FIFO along with a repeat of some of the above info.

### Receiving

Receiving bytes by a serial port is similar to sending them only it's in the opposite direction. It's also interrupt driven. For the obsolete type of serial port with 1-byte buffers, when a byte is fully received from the external cable it goes into the 1-byte receive buffer. Then the port gives the CPU an interrupt to tell it to pick up that byte so that the serial port will have room for storing the next byte, which is currently being received. For newer serial ports with 16-byte buffers, this interrupt (to fetch the bytes) may be sent after 14 bytes are in the receive buffer. The CPU then stops what it was doing, runs the interrupt service routine, and picks up 14 to 16 bytes from the port. For an interrupt sent when the 14th byte has been received, there could be 16 bytes to get if 2 more bytes have arrived since the interrupt. But if 3 more bytes should arrive (instead of 2), then the 16-byte buffer will overrun. It also may pick up less than 14 bytes by setting it that way or due to timeouts. See FIFOs for more details.

### The Large Serial Buffers

We've talked about small 16-byte serial port hardware buffers but there are also much larger buffers in main memory. When the CPU takes some bytes out of the receive buffer of the hardware, it puts them into a much larger (say 8k-byte) receive buffer in main memory. Then a program that is getting bytes from the serial port takes the bytes it's receiving out of that large buffer (using a "read" statement in the program). A similar situation exists for bytes that are to be transmitted. When the CPU needs to fetch some bytes to be transmitted it takes them out of a large (8k-byte) transmit buffer in main memory and puts them into the small 16-byte transmit buffer in the hardware.

## Enable USB-Serial Port adapter (RS-232)

## References

1. [What Are IRQ Numbers?](https://www.webopedia.com/quick_ref/IRQnumbers.asp)
2. [What is the difference between a baud rate and a bandwidth?](https://www.quora.com/What-is-the-difference-between-a-baud-rate-and-a-bandwidth)
3. [How are Serial Port Transmit Data and Receive Data?](https://www.pccompci.com/serial_port.html)
