# TCPdump: użycie filtrów standardowych z narzędzia oraz na podstawie headerów na protokół TCP
W tym repozytorium trzymam swoje notatki z nauki tcpdumpa i gotowe filtry do przeszukiwania ruchu sieciowego prosto z terminala.

## Co już ogarniam:
* Filtrowanie ruchu po konkretnym bajcie – wiem, jak za pomocą `tcp[13]` dobrać się do 14. bajtu w nagłówku TCP, gdzie siedzą flagi.
* Wyciąganie flag maskami bitowymi (`&`) – rozumiem wartości dziesiętne flag (np. SYN to 2, ACK to 16, a SYN-ACK to 18) i potrafię je wyłapać z ruchu.
* Tworzenie dokładnych filtrów – łączę warunki logiczne za pomocą `!= 0`, AND, OR oraz NOT, żeby program pokazał mi dokładnie te pakiety, o które mi chodzi.
* Szukanie konkretnych rzeczy w plikach pcap – potrafię namierzyć skanowanie portów (szukając flag RST i RST-ACK), a także analizować zapytania ARP czy DNS.
* **Cel / Wyzwanie:** Nauka przechwytywania i analizy ruchu sieciowego bez użycia interfejsu graficznego (GUI), bezpośrednio w terminalu systemowym, ze szczególnym uwzględnieniem zaawansowanych metod filtrowania poprzez odczytywanie konkretnych bajtów z nagłówków pakietów.

**Przebieg i Rozwiązanie:**

Znalezienie liczby pakietów używających protokołu ICMP.
![](screeny/20260620092413.png)

Znalezienie, jaki adres IP spytał się o adres MAC adresu IP 192.168.124.137. 
Odpowiedź to 192.168.124.148.
![](screeny/20260620092805.png)

Odnalezienie nazwy hosta pierwszego zapytania DNS. **Odpowiedź to mirrors.rockylinux.org.**
![](screeny/20260620093110.png)

Odczytanie, jaka liczba pakietów zawiera flagę TCP Reset (RST).
![](screeny/20260620100455.png)

Odczytanie wszystkich pakietów z flagą SYN.
![](screeny/20260620101348.png)

Znalezienie, jaki adres IP hosta wysyła pakiety większe niż 15000 bajtów.
![](screeny/20260620100259.png)
 
Jaki jest adres mac hosta, który wysłał zapytanie ARP.
![](screeny/20260620102055.png)

**Czego się nauczyłem:** Nauczyłem się analizy pakietów poprzez terminal wraz z różnymi opcjami filtrowania, na przykład ze względu na protokół transportowy, port, adresy docelowe i źródłowe.

Opanowałem filtrowanie zaawansowane poprzez nagłówki bajtów pakietów, głównie dla protokołu TCP.

Zrozumiałem, że w pakiecie flagi protokołu znajdują się na czternastym bajcie, co w pamięci komputera adresujemy jako indeks tcp[13] ze względu na liczenie od zera.

Zrozumiałem, że różne flagi danego protokołu są umieszczone na różnych bitach i mają swoje wartości dziesiętne.

Np.dowiedziałem się, że flaga ACK jest na bicie o wartości 16, a flaga SYN jest na bicie o wartości 2.

Zrozumiałem, dlaczego pakiet z połączonymi flagami SYN-ACK ma łączną wartość dziesiętną 18.

Nauczyłem się także przeprowadzania na tych flagach operacji logicznych przy użyciu bramek AND, OR oraz NOT podczas tworzenia filtrów.
