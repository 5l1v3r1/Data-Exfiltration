#!/usr/bin/env python
import logging
logging.getLogger("scapy.runtime").setLevel(logging.ERROR)
from scapy.all import *
import sys
import subprocess
import re


ip_add=sys.argv[1]
interface=sys.argv[2]
type_of_packet=sys.argv[3]
message=sys.argv[4]
messlen=len(message)
#print messlen

#Code referenced from StackOverflow---start
interfacesavail=subprocess.check_output("ifconfig", shell=True)
#print interfacesavail
x=re.findall(r'^(\S+).*?inet addr:(\S+).*?Mask:(\S+)', interfacesavail, re.S | re.M)
#Code referenced from StackOverflow---End

arrOfInterfaces=[]
for i in range(0,len(x)):
	arrOfInterfaces.append(x[i][0])
	#print x[i][0]
	
if interface not in arrOfInterfaces:
	print "Invalid Interface"
	sys.exit(0)
	
#Code referenced from StackOverflow---start
match = re.compile("^\d{1,3}\.\d{1,3}\.\d{1,3}\.\d{1,3}$")
result=re.search(match,ip_add)
#Code referenced from StackOverflow---End
if not result:
	print "Invalid IP"
	sys.exit(0)
	
#pack=IP(dst=sys.argv[1])/ICMP()
#send(pack)
#pack.show()



RandomID =random.randint(16,80)
#print "RandomID"  , RandomID
for i in range (0,messlen) :
	#print message[i]
	hexval=hex(ord(message[i]))
	hexval=hexval[2:]
	#RandomID=int(RandomID)
	hexRandom=hex(RandomID)
	hexRandom=hexRandom[2:]
	#print hexRandom
	#print hexval
	#print letter
	x=str(hexval)+str(hexRandom)
	#print "Concatenat", x
	decval=int(x, 16)
		
		
	pos=i
	pos=hex(pos)[2:]
	pos=pos.zfill(3)
	fragpos=pos.zfill(4)
	#print fragpos
	#fragpos=str("0")+str(pos)
	#fragpos=hex(fragpos)
	#print "hexfrag" , fragpos
	fragpos=int(fragpos, 16)
	#print "decfrag" , fragpos
	if type_of_packet=='0':
		pack=IP(dst=ip_add,id=decval,frag=fragpos)/ICMP()
		send(pack,iface=interface)
		pack.show()
	elif type_of_packet=='1':
		pack=IP(dst=ip_add,id=decval,frag=fragpos)/TCP(dport=80,flags="S")
		send(pack,iface=interface)
		pack.show()
	elif type_of_packet=='2':
		pack=IP(dst=ip_add,id=decval,frag=fragpos)/UDP(dport=53)
		send(pack,iface=interface)
		pack.show()
	else:
		print "Invalid type"
		sys.exit(0)

#print "i final val" , i		
hexzero=hex(0)
#print hexzero
hexzero=hexzero[2:]
hexzero=hexzero.zfill(2)
#print hexzero
x=str(hexzero)+str(hexRandom)
#print "Concatenat", x
decval=int(x, 16)
#print decval

pos=i
pos=pos+1
#print "pos" , pos
pos=hex(pos)[2:]
pos=pos.zfill(3)
fragpos=str("1")+str(pos)
#print fragpos
fragpos=int(fragpos, 16)
#print "decfrag" , fragpos
if type_of_packet=='0':
	pack=IP(dst=ip_add,id=decval,frag=fragpos)/ICMP()
	send(pack,iface=interface)
	pack.show()
elif type_of_packet=='1':
	pack=IP(dst=ip_add,id=decval,frag=fragpos)/TCP(dport=80,flags="S")
	send(pack,iface=interface)
	pack.show()
elif type_of_packet=='2':
	pack=IP(dst=ip_add,id=decval,frag=fragpos)/UDP(dport=53)
	send(pack,iface=interface)
	pack.show()
else:
	print "Invalid type"
	sys.exit(0)
		
