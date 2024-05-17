**Задание 1.**

*Проведите разведку системы и определите, какие сетевые службы запущены на защищаемой системе:*

*sudo nmap -sA < ip-адрес >*

*sudo nmap -sT < ip-адрес >*

*sudo nmap -sS < ip-адрес >*

*sudo nmap -sV < ip-адрес >*

**Решение 1.**

При сканировании nmap -sA мы проверяем нет ли фаервола на удаленной машине.
Здесь в логах ничего не срабатыает ни в Suricata ни в Fail2ban

![alt text](https://github.com/mezhibo/Defender-network/blob/dd2c638d5d0019f7a2e861aaa13a8eac9123b5bc/IMG/11.jpg)



При сканировании nmap -sT мы сканируем все TCP-порты, и вот здесь уже Suricata в логах видит что нас сканируют

![alt text](https://github.com/mezhibo/Defender-network/blob/dd2c638d5d0019f7a2e861aaa13a8eac9123b5bc/IMG/12.jpg)

![alt text](https://github.com/mezhibo/Defender-network/blob/dd2c638d5d0019f7a2e861aaa13a8eac9123b5bc/IMG/1.jpg)

Fail2ban по прежнему молчит


При запуске скрытого сканирования nmap -sS в логах мытоже видими что нас сканируют

![alt text](https://github.com/mezhibo/Defender-network/blob/dd2c638d5d0019f7a2e861aaa13a8eac9123b5bc/IMG/13.jpg)

![alt text](https://github.com/mezhibo/Defender-network/blob/dd2c638d5d0019f7a2e861aaa13a8eac9123b5bc/IMG/2.jpg)

Fail2ban по прежнему молчит



При сканировании nmap -sV мы пытаемся узнать что за службы запущены на портах

![alt text](https://github.com/mezhibo/Defender-network/blob/dd2c638d5d0019f7a2e861aaa13a8eac9123b5bc/IMG/14.jpg)

Suricata все пишет в Лог

![alt text](https://github.com/mezhibo/Defender-network/blob/dd2c638d5d0019f7a2e861aaa13a8eac9123b5bc/IMG/3.jpg)

Fail2ban по прежнему пуст


Теперь ради интереса просто проведем пинг с атакующей машины и посмотрим логи атакуемой машины, увидит ли suricata что машину сканировали на работоспособность в сети 

![alt text](https://github.com/mezhibo/Defender-network/blob/dd2c638d5d0019f7a2e861aaa13a8eac9123b5bc/IMG/15.jpg)

![alt text](https://github.com/mezhibo/Defender-network/blob/dd2c638d5d0019f7a2e861aaa13a8eac9123b5bc/IMG/4.jpg)

Как видно в логах, suricata все видит




*Вывод*

Логи fail2ban пусты потому что это система предотвращения вторжений (Intrusion prevention systems, IPS) и
она в логи будет писать попытки вторжени я в машину

А логи suricata пишутся потому что это система обнаружения вторжений (Intrusion detection system, IDS) и
ее задача писать в логи и отслеживать все попытки обнаружения возможных подключений









