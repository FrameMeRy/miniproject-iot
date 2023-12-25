# ชื่อโครงการ: BB Payment (bangbank)

## สมาชิกในกลุ่ม
- 64120280 รัชชานนท์ ชูเกียรติเถกิง 
- 64102288 จิรายุ สาสนทาญาติ 
- 64117039 ทีปกร ตระกูลกลกิจ

## บทนำ
<br>&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;ทางกลุ่มผู้จัดทำโครงการสนใจเรื่องระบบชำระเงินผ่านบัตรและความสะดวกสบายของมนุษย์ ซึ่งการชำระเงินผ่านบัตรจะช่วยอำนวยความสะดวกสบายให้กับมนุษย์โดยจะเพิ่มความรวดเร็วให้กับการซื้อขายต่างๆเพื่อเป็นแนวทางการลดขั้นตอนและเพิ่มความรวดเร็วให้กับการซื้อขาย
<br>&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;เนื่องด้วยปัจจุบันมนุษย์นั้นมีจำนวนมากขึ้นส่งผลให้สถานที่ที่มีขนาดจำกัดอัดแน่ไปด้วยมนุษย์หากเกิดความล่าช้าในกระบวนการต่างๆส่งผลให้มนุษย์นั้นไม่สะดวกสบาย ดั้งนั้นผู้จัดทำจึงมุ่งเน้นในการผลิตอุปกรณ์ IoT ที่สามารถลดขั้นตอนกระบวนการการซื้อ ขายเพื่อเป็นหนึ่งในตัวช่วยในการลดกระบวนการและเพิ่มความรวดเร็วให้กับกระบวนการดังกล่าว
<br>&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;ทางผู้จัดทำโครงงานจึงพัฒนาอุปกรณ์ IoT ที่สามารถชำระเงินผ่านระบบRFID โดยมีข้อมูลที่เก็บเป็นชื่อของผู้ใช้บัตร จำนวนเงิน ไอดี และส่วนที่เป็นสิ้นค้าจะมีชื่อสินค้า ราคา

## การออกแบบระบบ


![System](https://drive.google.com/uc?id=1Pic7np83KYsHdboHVI8eHc9xhwm-jWYE)

#### Collecter Layer เป็นส่วนของการรับข้อมูลจาก RFID เพื่อนำร่วมในการประมวนผลในขั้นตอนต่อไป

#### Processing Layer เป็นส่วนของการเก็บข้อมูล โดยฐานข้อมูลที่เลือกใช้นั้นจะเป็น Json Server และมีตัวกลางในการเชื่อมต่อกับฝั่ง Frontend โดยใช้ Flask 

#### Frontend Layer  เป็นส่วนของการแสดงผลโดยจะนำข้อมูลจาด Json Sever ที่ประกอบด้วย id, Pname, Price มาร่วมในการแสดงเพื่อทำการชำระเงิน


![3](https://github.com/FrameMeRy/miniproject-iot/assets/102577717/d2ee909f-5a3f-4415-8dfb-6d884edb449d)

#### Collecter Layer 
- Arduino เป็นบอร์ดในการรับค่าข้อมูลจาก RFID เพื่อส่งไปให้ ESP8266
- ESP8266 ใช้สำหรับในการรับค่าจาก Arduino และนำส่งข้อมูลที่ได้ไปยัง MQTT
#### Processing Layer
- MQTT ใช้สำหรับในการรับข้อมูลจาก ESP8266 และส่งข้อมูล ไปยัง Flask เพื่อใช้ในการตรวจสอบ ID ที่ใช้ในการจ่ายเงิน
- Flask ใช้ในการรับ ID ไปใช้ในระบบจ่ายเงิน รวมถึงการรับข้อมูลสินค้าที่เลือกจากผู้ใช้ และแสดงผลใน Web Frontend
- JSON เป็น database ที่ใช้ในการเก็บข้อมูลของเจ้าของบัตรและจำนวนเงิน
#### Frontend Layer
- Frontend มีหน้าที่ในการแสดงผลและส่งข้อมูลสินค้าที่เลือกไปยัง Flask หรือ Web API



## Data Stucture
โครงสร้างข้อมูลจะถูกจัดเก้บในส่วนของ Json ที่จะประกอบไปด้วยข้อมูลของบัตร ดังนี้ id,Name,Money 

#### ส่วนของบัตร (CInformation):
```json
{
    "CInformation": [
        {
            "id": 1,
            "Name": "Frame",
            "Money": 300
        },
        {
            "id": 2,
            "Name": "Bank",
            "Money": 300
        }
    ]
}

```

## Data Dictionary

| Attribute | Description | Data Type | Example |
|--------------------|--------------------|--------------------|--------------------|
| id  | รหัสของผู้ใช้งาน  | int   | 1   |
| Name  |  ชื่อของผู้ใช้  | String   | bang   |
| Money  |เงินของผู้ใช้  | int   | 100   |

## การพัฒนาระบบ
### เครื่องมือ 
1) ATmega328P WiFi ESP8266+8Mb flash ทำหน้าที่ในการรับค่าจาก RFID และส่งต่อไปยัง MQTT 
2) RFID-RC522 ใช้สำหรับในการสแกนบัตรจ่ายเงิน


### ภาษาโปรแกรม
1) ภาษา C ใชในการเขียนคำสั่งลงไปยัง Board เพื่อที่จะสามารถรับค่าและส่งค่าข้อมูลได้
2) JSON เป็นภาษาในการแลกเปลี่ยนข้อมูล ใช้ในการเป็น server ในการรับค่าจาก Board เพื่อใช้เป็นสื่อกลางข้อมูลระหว่าง Board website และ MQTT
3) JavaScrip ใช้ในการดึงข้อมูลจาก Json server เพื่อนำไปแสดงผลบนหน้า website 
4) HTML  เป็นภาษามาร์กอัปที่ใช้ในการสร้างหน้าเว็บใช้ในการ ทำ website เพื่อใช้ในการแสดงผลโดยจะอยู่ในั่ง Front end
5) ภาษา Python เป็นภาษาที่ใช้เขียนคำสั่งในการชำระเงิน และดึงข้อมูลผ่าน Mqtt
6) CSS ภาษาที่ใช้สำหรับการแสดงผลและการจัดรูปแบบของเว็บไซต์หรือเอกสาร


### ไลบรารี
1) paho.mqtt เป็นไลบรารี่เชี่ยมต่อกับ MQTT ในการรับส่งข้อมูล
2) flask เป็นเว็ป framework python สำหรับ web app 
## การทดสอบ  

การทดลองในสถานการณ์ 1 ทดลองนำ บัตรของเราไปทดลองจ่ายเงิน <br>
การทดลองในสถานการณ์ 2 ทดลองนำ บัตรอื่นไปทดลองจ่ายเงิน 


## สรุปผลการทดสอบ

ตัวระบบสามารถใช้ชำระผ่านตัวของ RFID แสดงให้เห็นถึงการลดขั้นตอนในกระบวนการซื้อขายได้ตามวัตถุประสงค์ของตัวโครงงาน


