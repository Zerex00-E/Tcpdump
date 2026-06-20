# TCPdump: użycie filtrów podstawowych od narzędzia oraz na podstawie headerów protokołu TCP

**Cel / Wyzwanie:** Nauka przechwytywania i analizy ruchu sieciowego bez użycia interfejsu graficznego (GUI), bezpośrednio w terminalu systemowym, ze szczególnym uwzględnieniem zaawansowanych metod filtrowania poprzez odczytywanie konkretnych bajtów z nagłówków pakietów TCP.

**Przebieg i Rozwiązanie:**

Znalezienie liczby pakietów używających protokołu ICMP.
![](screeny/Pasted%20image%2020260620092413.png)

Znalezienie, jaki adres IP spytał się o adres MAC adresu IP 192.168.124.137. 
**Odpowiedź to 192.168.124.148.**
![](screeny/Pasted%20image%2020260620092805.png)

Odnalezienie nazwy hosta pierwszego zapytania DNS. **Odpowiedź to mirrors.rockylinux.org.**
![](screeny/Pasted%20image%2020260620093110.png)

Odczytanie, jaka liczba pakietów tylko zawiera flagę TCP Reset (RST).
![](screeny/Pasted%20image%2020260620100455.png)

Odczytanie pięciu pakietów z flagą SYN.
![](screeny/Pasted%20image%2020260620101348.png)

Znalezienie, jaki adres IP hosta wysyła pakiety większe niż 15000 bajtów.
![](screeny/Pasted%20image%2020260620100259.png)
 
Jaki jest adres mac hosta, który wysłał zapytanie ARP.
![](screeny/Pasted%20image%2020260620102055.png)

**Czego się nauczyłem:** Nauczyłem się analizy pakietów poprzez terminal wraz z różnymi opcjami filtrowania, na przykład ze względu na protokół transportowy, port, adresy docelowe i źródłowe.

Opanowałem filtrowanie zaawansowane poprzez nagłówki bajtów pakietów, głównie dla protokołu TCP.

Zrozumiałem, że flagi protokołu znajdują się na czternastym bajcie nagłówka TCP, co w pamięci komputera adresujemy jako indeks tcp[13] ze względu na liczenie od zera.

Zrozumiałem, że różne flagi danego protokołu są umieszczone na różnych bitach i mają swoje wartości dziesiętne.

Np. dowiedziałem się, że flaga ACK jest na bicie o wartości 16, a flaga SYN jest na bicie o wartości 2.

Zrozumiałem, dlaczego pakiet z połączonymi flagami SYN-ACK ma łączną wartość dziesiętną 18.

Nauczyłem się także przeprowadzania na tych flagach operacji logicznych przy użyciu bramek AND, OR oraz NOT podczas tworzenia filtrów.
