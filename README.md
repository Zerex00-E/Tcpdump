# TCPdump: użycie filtrów standardowych z narzędzia oraz na podstawie headerów na protokół TCP
W tym repozytorium trzymam swoje notatki z nauki tcpdumpa i gotowe filtry do przeszukiwania ruchu sieciowego prosto z terminala.

## Co już ogarniam:
* Filtrowanie ruchu po konkretnym bajcie – wiem, jak za pomocą `tcp[13]` dobrać się do 14. bajtu w nagłówku TCP, gdzie siedzą flagi.
* Wyciąganie flag maskami bitowymi (`&`) – rozumiem wartości dziesiętne flag (np. SYN to 2, ACK to 16, a SYN-ACK to 18) i potrafię je wyłapać z ruchu.
* Tworzenie dokładnych filtrów – łączę warunki logiczne za pomocą `!= 0`, AND, OR oraz NOT, żeby program pokazał mi dokładnie te pakiety, o które mi chodzi.
* Szukanie konkretnych rzeczy w plikach pcap – potrafię namierzyć skanowanie portów (szukając flag RST i RST-ACK), a także analizować zapytania ARP czy DNS.