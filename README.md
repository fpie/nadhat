Welcome to Nadhat.
==================

Nadhat is a GSM/GPRS modem hat for raspberry pi. It's pi zero hat format compatible (30x65mm). It uses the well known SIM800C module to offer a lost M2M communication interface.

You'll find in this deposit datasheets and application notes, some pieces of firmware and more in the future.

You can also follow nadhat google+ collection : https://plus.google.com/collection/o2lZRE

Have fun.

Frederic Pierson


Don't wan't to read the manual, here a quickstart guide :

default setup for serial port /dev/ttyAMA0 is 115200,8,N,1

Some usefull at command for SIM800C :
====================================
at : answer OK is serial setup is OK
atz : reset default configuration
ati : display product indentification information
at+cgmi : display product manufacturer
at+cgmm : display model identification
at+cpin? : check if pin number is required
at+cpin=xxxx : enter pin code
at+cbc : battery voltage (around 67% or 3940mV)
at&v : display current configuration
at+csq : report quality of signal (first nb between 0-31, 2nd nb between 0-7, bigger is better)
at+gsn : request TA serial Number Identification (IMEI)
at+cimi : request international subscriber identity
at+cops=? : report list of present operators
at+cspn? : get service provider name from sim
at+cadc? : read adc input (0-2.8V range, pin 7 of CN2)
at+cpowd=1 : normal poweroff

Send an SMS :
=============
at+cmgf=1 : sms in text mode
at+csca="+33695000695" : service provider sms center number (french provider FREE for me)
at+cmgs="+3363054xxxx" : start SMS edition to "receiver number"
>>> prompt become '>'
input your SMS + <CR>
send hexadecimal chars '0x1A,0x0D' (<SUB><CR> in fact) to send your SMS

Receive an SMS :
================
at+cmgd=1 : delete sms slot 1 (free slot after that)
>>> answer the SMS you've received on your phone by Nadhat.
>>> should receive 'CMTI:"SM",1' meaning you have receive a SMS in slot 1
at+cmgr=1 : read sms in slot 1
at+cmgd=1 : delete sms to free again slot 1 for next SMS



