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


Collecter Layer เป็นส่วนของการรับข้อมูลจาก RFID เพื่อนำร่วมในการประมวนผลในขั้นตอนต่อไป

Processing Layer เป็นส่วนของการเก็บข้อมูล โดยฐานข้อมูลที่เลือกใช้นั้นจะเป็น Json Server และมีตัวกลางในการเชื่อมต่อกับฝั่ง Frontend โดยใช้ Flask 

Frontend Layer เป็นส่วนของการแสดงผลโดยจะนำข้อมูลจาด Json Sever ที่ประกอบด้วย id, Pname, Price มาร่วมในการแสดงเพื่อทำการชำระเงิน

![Software](https://drive.google.com/uc?id=1sKEWH6LqLT-iAbHmVHN1A9L140QO1RpL)

Ari

## Data Stucture
โครงสร้างข้อมูลจะถูกจัดเก้บในส่วนของ Json ที่จะประกอบไปด้วยข้อมูล 2 ส่วนของโดยจะส่วนของบัตรมีดังนี้ id,Name,Money และช่วนของสิ้นค้ามีดังนี้ id,Pname,Price ดังตัวอย่างตามลำดับ

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
#### ส่วนของสินค้า
```json
[
    {
      "id": 1,
      "Pname": "น้ำดื่มสะอาด",
      "Price": 15
    },
]
```
## Data Dictionary

| Attribute | Description | Data Type | Example |
|--------------------|--------------------|--------------------|--------------------|
| id  | รหัสของผู้ใช้งาน  | int   | 1   |
| Name  |  ชื่อของผู้ใช้  | String   | bang   |
| Money  |เงินของผู้ใช้  | int   | 100   |
| id    |id ของสินค้า | int | 1 |
| Pname | ชื่อของสินค้า | String | น้ำ |
| Price | ราคาของสินค้า  | int | 10 |
## การพัฒนาระบบ
### เครื่องมือ 
1) VS code IDE เป็น Editer ในการพัฒนาส่วนที่อยู่นอกบอร์ด

### ภาษาโปรแกรม
1) ภาษา C ภาษาที่ใช้ในการเขียนคำสั่งลงไปยัง Board
2) Json เป็นภาษาในการแลกเปลี่ยนและเก็บข้อมูล ใช้ในการเป็น server 
3) ภาษา python เป็นภาษาที่ใช้เขียนคำสั่งในการชำระเงิน และดึงข้อมูลผ่าน Mqtt
4) javascipt เป็นภาษาในการสั่งการทำงานส่วนต่างๆบนหน้าเว็ปไซต์
5) html เป็นภาษาในการสร้างหน้าเว็ปไซต์
6) css เป็นภาษาในการตกแต่งหน้าเว็ปไซต์


### ไลบรารี

## การทดสอบ   
## สรุปผลการทดสอบ


