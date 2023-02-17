# ping-pong-launcher
Code for Streamer.Bot Ping Pong Launcher

Please watch the YouTube video for an explanation and to set it up:
https://youtu.be/WCyJONnICOI



The below text is to import the action into Streamer.Bot:
```
TlM0RR+LCAAAAAAABACdVltzokgUfp+q+Q+uz2uKqwlTNQ+Cippoggoi6zz0TSQ2NMtFxan579tATLwkL2sVpZ7vXL/T9Dm/v39rNJo7kqQBi5o/GtLflSACIeH/mi9B5DdeWOQ3azlAGddLOfRP+b/R+F1/cSjApUFblERMVNxCaw23FPVBaT0AILbabVkFoqqs+VftqzL6Nyd5GSjKKf2QkghASkp/WZKTM/kB0RyTfsLCQZBmLCm4yhrQ9EznlPlsw1jWeM+/oQNKzwL7CcvjUm/em83P5IDuQZFO8+jWcwIizMJOxcAtiliE8iQhUXaL3bB2wdxl2iTCjWxDGiFJU+CTRsYaaVVKKYQXRVSGmKQoCeK3pJpX6JaQuEODHblJqi6JrAlPGZGr3CrQ+LFaLQJe8z5drcYBSljK1tndpDdfrfoJz3fPkm1bWa12yp1wJwuyqK1WYYpYQgN4h3mm5w5/XUaGRUYMhquasTuJYYh8W6ZHbDrZ8154vJY9bVWKu+nEiJwjWKjRsD9RkTylcKbanrsRvrQx1DmUJonnTo+lTteK93gxSsFi7C+lwwbJY98S9eFsoXKZSjl+37XYCA2cAJr0dWiOdlDa+1N3Q5eyI3gzPy5xwn0ZFo8zGFUxHXtquQK1hl3BH7721HGgHCavfv7cXebjbid4Ljq7p0I/eq7lA/5g88H3TIfnSfOlO42hpPgzp5M/BfrMNrc+WChcZxOjQn9duhNaxjQW/PQbujPt62u7p80co6MNu71ifLTEujauY092MOKPaeeOPIo5D+OyrkdjxO063Ge/8CRHGPao9Rx0gqGRvuf+OOf8+tuRJWk5krTUm6kuCqng2Qdeo82G1OnZhi4s3VFU1oFMrcBd5g+DTjLsc6yvWXNxZNd+Kn6kpTv0OW8FCp0c93mdC9t/mek9XjN1TJrxGM9QRrljavM3Ltkpj1M/HwfeBgX6sexjyS8MHZn3f7eUMt7fje6Z08JzJ8dp2M/A4qA+bTlPplPMQ0fAklaAYu/bkvYKeN3OgO55zJ4njzZwxuWD0Q6b2iuUDjZxdfpEnS0ytlWPDbfOw3DLWGluS07u9ae7x56TLyVtW55Drm9PeZ+n3LcVca7cMedJr8+hqeVeoRvLxSHl+TIoW/7TrOb8ipP4ydBzz0X8DOh9GE4tKJW93ozsXn/rDUaUn9Pc5r1Dks3e+8Xzr36L+otNrfjE29p6OwvuiOKBU8BAF1Dk0PKMGK7A3yH++D9/Xt0VcUIQC+OAfnFZYEJBMctAcnvDVXgKdmRK0pxmc+aAJCjv8K81L3Sur616lsB7DeL7e7GlKQ+opQhQaIF7ILTaRBUgFAFe34Mrwz0J/E2Zn3AnXCJZEZeRtPJziZxGwcUMqpAv5lCdYoTJoQz0If1z+vnr+uo3yxDVHfvrfGJQCuKU4DO0BitHtWY9Ic9MuVkY8kn06QxOWZ7cXObnRIifpBiTJAyyjGA75WvAVZLv4Kcl1H1ScRvKbSS1OLUPLUVWlBaEstBSJOUBilhpE4ibn033qzEZRNV4vxn7YT0nhHPqKg7K4H+BLANo27ymfPh/1hHEGOXzLup8uLjcTChD4G3UimeJ+xFLiM6yDkIsrzaAywricr9KM6MESfLZ8nAChBujsitfGuYfYNmb33/OfIKU8G0iDbLPxn/Tp4xvE8ZbwRxvC9du3yHx4Qx735wutikQZfP6DRPOz/D3b3/+A5kbC5tiCgAA
```


Here is the python code:

```
import socket
import RPi.GPIO as GPIO
import time

UDP_IP = "0.0.0.0" # listen to everything
UDP_PORT = 12345 # port

in2 = 7  # the number 7 is for pin#7 which is GPIO #4
GPIO.setwarnings(False)
GPIO.setmode(GPIO.BOARD)
GPIO.setup(in2, GPIO.OUT)

GPIO.output(in2, True)

sock = socket.socket(socket.AF_INET,socket.SOCK_DGRAM)
sock.bind((UDP_IP, UDP_PORT))

while True:
    data, addr = sock.recvfrom(512) # random buffer size, doesn't matter here..
    print("received message:", data)
    GPIO.output(in2, False)
    time.sleep(2.1)
    GPIO.output(in2, True)

    GPIO.cleanup
```

Installing GPIO: https://www.raspberrypi-spy.co.uk/2012/05/install-rpi-gpio-python-library/


