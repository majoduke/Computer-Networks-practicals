# Computer-Networks-practicals

Q1.Simulate and implement stop and wait protocol for noisy channel.

Simplex Stop – and – Wait protocol for noisy channel is data link layer protocol for data communications with error control and flow control mechanisms.It is popularly known 
as Stop – and –Wait Automatic Repeat Request (Stop – and –Wait ARQ) protocol. It adds error control facilities to Stop – and – Wait protocol. This protocol takes into account 
the fact that the receiver has a finite processing speed and that frames may get corrupted while transmission. If data frames arrive at the receiver’s end at a rate which is 
greater than its rate of processing, frames can be dropped out. Also, frames may get corrupted or entirely lost when they are transmitted via network channels. So, the receiver
sends an acknowledgement for each valid frame that it receives.The sender sends the next frame only when it has received a positive acknowledgement from the receiver that it is 
available for further data processing.Otherwise, it waits for a certain amount of time and then resends the frame.

Design
Sender Site −
At the sender site, a field is added to the frame to hold a sequence number. If data is available, the data link layer makes a frame with the certain sequence 
number and sends it. The sender then waits for the arrival of acknowledgement for a certain amount of time. If it receives a positive acknowledgement for the frame with that
sequence number within the stipulated time, it sends the frame with the next sequence number. Otherwise, it resends the same frame.

Receiver Site − 
The receiver also keeps a sequence number of the frames expected for arrival. When a frame arrives, the receiver processes it and checks whether it is valid or
not. If it is valid and its sequence number matches the sequence number of the expected frame, it extracts the data and delivers it to the network layer. It then sends an
acknowledgement for that frame back to the sender along with its sequence number.







Q2.Simulate and implement selective repeat sliding window protocol.

Why Selective Repeat Protocol?
The go-back-n protocol works well if errors are less, but if the line is poor it wastes a lot of bandwidth on retransmitted frames. An alternative strategy, the selective 
repeat protocol, is to allow the receiver to accept and buffer the frames following a damaged or lost one.

Selective Repeat attempts to retransmit only those packets that are actually lost (due to errors) :
-The receiver must be able to accept packets out of order.
-Since the receiver must release packets to higher layer in order, the receiver must be able to buffer some packets.

Retransmission requests :
Implicit – 
The receiver acknowledges every good packet, packets that are not ACKed before a time-out are assumed lost or in error. Notice that this approach must be used to 
be sure that every packet is eventually received.

Explicit – 
An explicit NAK (selective reject) can request retransmission of just one packet. This approach can expedite the retransmission but is not strictly needed.
One or both approaches are used in practice.

Selective Repeat Protocol (SRP) :
This protocol(SRP) is mostly identical to GBN protocol, except that buffers are used and the receiver, and the sender, each maintains a window of size. SRP works better when 
the link is very unreliable. Because in this case, retransmission tends to happen more frequently, selectively retransmitting frames is more efficient than retransmitting all 
of them. SRP also requires full-duplex link. backward acknowledgements are also in progress.
-Sender’s Windows ( Ws) = Receiver’s Windows ( Wr).
-Window size should be less than or equal to half the sequence number in SR protocol. This is to avoid packets being recognized incorrectly. If the size of the window is greater 
than half the sequence number space, then if an ACK is lost, the sender may send new packets that the receiver believes are retransmissions.
-Sender can transmit new packets as long as their number is with W of all unACKed packets.
-Sender retransmit un-ACKed packets after a timeout – Or upon a NAK if NAK is employed.
-Receiver ACKs all correct packets.
-Receiver stores correct packets until they can be delivered in order to the higher layer.
-In Selective Repeat ARQ, the size of the sender and receiver window must be at most one-half of 2^m.
