# Router hardening record -- SCS4.1

Date: 2026-11-25
Station and router (the kit station's router, never the campus): SA isolated kit station router (gateway 10.10.51.1)
Admin page address (the router's own address): http://10.10.51.1
DHCP range: [check router settings or screenshot for pool start-end]
Firmware date seen on the router: [check router status/firmware page or not done: not checked]

Tick a line [x] only when it is done and checked.  A line not done says why, on the same line.
Never write a password here.  The admin password and the wifi passphrase go on the owner's card, and on the
kit the owner's card goes to the SA.  The screenshot goes to ~/scs/evidence/scs4.1, checked for passwords first.

1. [ ] Admin password changed from the default, on the owner's card, nowhere on the wall -- not done: [confirm whether changed and recorded on owner's card only]
2. [ ] Wifi on WPA2 or WPA3 with a long passphrase -- three words and a number, not the shop's phone number -- not done: [confirm WPA2/WPA3 passphrase status]
3. [ ] Network name gives away neither the router model nor the owner's name -- not done: [confirm SSID name]
4. [ ] A guest network for customers, so the till and the printer are not on the strangers' wifi -- not done: [confirm guest network status]
5. [ ] DHCP range noted; the printer's address reserved on the router (or fixed on the printer outside the range) -- not done: [confirm DHCP reservation/fixed IP]
6. [ ] WPS off; remote admin from the internet off -- not done: [confirm WPS and remote admin settings]
7. [ ] Firmware date noted; an update only if the SA says it is safe today -- not done: [confirm firmware check]
8. [ ] Router restarted afterwards and the four numbers read again on a laptop -- still right -- not done: [confirm post-restart check]

## The printer

Printer's address (from its own panel or test page): [printer IP or not done: no printer address recorded]
Reserved on the router (yes / no): not done: [confirm reservation]
Added on a lab laptop by address, test page printed (yes / no): not done: [no test page printed yet]
Added on a phone, test page printed (yes / no): not done: [no test page printed yet]
Router restarted without the reservation first -- what happened: not done: not performed
Second look, the next SCS track day -- still at its address after the SAs' power-off (yes / no): not done: next track day
Anything mechanical, named and referred (not opened): none observed / not opened
