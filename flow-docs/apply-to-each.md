---
title: ใช้การดำเนินการ นำไปใช้ในแต่ละอัน เพื่อวนรอบไปตามอาร์เรย์ของรายการ | Microsoft Docs
description: ใช้ Microsoft Flow เพื่อวนรอบไปตามอาร์เรย์ของรายการ เพื่อตรวจสอบเงื่อนไขหลายเงื่อนไข และดำเนินการตามเงื่อนไขเหล่านั้น
services: ''
suite: flow
documentationcenter: na
author: msftman
manager: anneta
editor: ''
tags: ''
ms.service: flow
ms.devlang: na
ms.topic: article
ms.tgt_pltfrm: na
ms.workload: na
ms.date: 03/16/2017
ms.author: deonhe
ms.openlocfilehash: 37f1ce939db23694bcd92e7f1af75bf6c474be91
ms.sourcegitcommit: 945614d737d5909c40029a61e050302d96e1619d
ms.translationtype: HT
ms.contentlocale: th-TH
ms.lasthandoff: 06/04/2018
ms.locfileid: "31001284"
---
# <a name="use-the-apply-to-each-action-in-microsoft-flow-to-process-a-list-of-items-periodically"></a>ใช้การดำเนินการ นำไปใช้ในแต่ละอัน ใน Microsoft Flow เพื่อประมวลผลรายการของข้อมูลเป็นระยะ ๆ
หลาย ๆ ทริกเกอร์สามารถเริ่มต้นโฟลว์ทันทีตามเหตุการณ์ เช่นเมื่อมีอีเมลใหม่เข้ามาในกล่องขาเข้าของคุณ ทริกเกอร์เหล่านี้ดีเยี่ยม แต่บางครั้งคุณต้องการเรียกใช้โฟลว์ที่คิวรีแหล่งข้อมูลตามเวลาที่กำหนดไว้ล่วงหน้า และดำเนินการบางอย่างขึ้นอยู่กับคุณสมบัติของรายการในแหล่งข้อมูล ในกรณีนี้ โฟลว์ของคุณจะเริ่มต้นตามกำหนดเวลา (เช่น วันละครั้ง) และใช้การดำเนินการแบบวนรอบเช่น **นำไปใช้ในแต่ละอัน** (apply to each) เพื่อประมวลผลรายการของข้อมูล ตัวอย่างเช่น คุณสามารถใช้ **นำไปใช้ในแต่ละอัน** เพื่ออัปเดตระเบียนจากฐานข้อมูลหรือรายการจาก Microsoft SharePoint ได้

ในนี้การฝึกปฏิบัตินี้ เราจะสร้างโฟลว์ที่ทำงานทุก 15 นาที และทำสิ่งต่อไปนี้:

1. รับข้อความที่ยังไม่ได้อ่าน 10 ข้อความล่าสุดในกล่องจดหมายเข้า Office 365 Outlook
2. ตรวจสอบทั้ง 10 ข้อความเพื่อยืนยันว่ามีข้อความ **meet now** ในชื่อเรื่องหรือไม่
3. ตรวจสอบว่า อีเมลมาจากเจ้านายของคุณ หรือส่งโดยมีความสำคัญสูง
4. ส่งการแจ้งเตือน และทำเครื่องหมายว่าอ่านอีเมลแล้ว สำหรับอีเมลใด ๆ ที่มีข้อความ **meet now** ในชื่อเรื่อง และมาจากเจ้านายของคุณ หรือส่งโดยมีความสำคัญสูง

ไดอะแกรมนี้แสดงรายละเอียดของโฟลว์ที่เราจะสร้างในการฝึกปฏิบัตินี้:

![ภาพรวมของโฟลว์จะสร้างขึ้น](./media/apply-to-each/foreach-flow-visio.png)

## <a name="prerequisites"></a>ข้อกำหนดเบื้องต้น
นี่คือข้อกำหนด เพื่อทำตามขั้นตอนในการฝึกปฏิบัตินี้ให้สำเร็จ:

* บัญชีผู้ใช้ที่ลงทะเบียนเพื่อใช้ [Microsoft Flow](https://flow.microsoft.com)
* บัญชีผู้ใช้ Office 365 Outlook
* แอปสำหรับอุปกรณ์เคลื่อนที่ Microsoft Flow [Android](https://aka.ms/flowmobiledocsandroid), [iOS](https://aka.ms/flowmobiledocsios) หรือ [Windows Phone](https://aka.ms/flowmobilewindows)
* การเชื่อมต่อกับ Office 365 Outlook และบริการการแจ้งเตือนแบบพุช

## <a name="create-a-flow"></a>สร้างโฟลว์
1. ลงชื่อเข้าใช้ [Microsoft Flow](https://flow.microsoft.com)
2. เลือกแท็บ**โฟลว์ของฉัน** จากนั้นสร้างโฟลว์จากว่างเปล่า:
   
    ![สร้างจากว่างเปล่า](./media/apply-to-each/foreach-1.png)
3. ใส่ "กำหนดการ" ลงในกล่องค้นหาเพื่อค้นหาบริการและทริกเกอร์ทั้งหมด ที่เกี่ยวข้องกับการกำหนดเวลา
4. เลือกทริกเกอร์ **กำหนดการ - การเกิดขึ้นประจำ** เพื่อระบุว่า โฟลว์ของคุณจะทำงานตามกำหนดเวลาที่คุณจะกำหนดต่อไป:
   
    ![การดำเนินการ กำหนดการที่เกิดขึ้นประจำ](./media/apply-to-each/foreach-2.png)
5. ตั้งค่ากำหนดเวลาการทำงานทุก 15 นาที:
   
    ![กำหนดเวลาการทำงาน](./media/apply-to-each/foreach-3.png)
6. เลือก **+ ขั้นตอนใหม่**, **เพิ่มการดำเนินการ** และจากนั้น พิมพ์ **outlook** ลงในกล่องค้นหา เพื่อค้นหาการดำเนินการทั้งหมดที่เกี่ยวข้องกับ Microsoft Outlook
7. เลือกการดำเนินการ **Office 365 Outlook - รับอีเมล**:
   
    ![เลือกการดำเนินการรับอีเมล](./media/apply-to-each/foreach-4.png)
8. ซึ่งจะเปิดการ์ด**รับอีเมล** กำหนดค่าการ์ด**รับอีเมล** เพื่อเลือกอีเมลที่ยังไม่ได้อ่านล่าสุด 10 อีเมลจากโฟลเดอร์กล่องขาเข้า ไม่รวมไฟล์แนบ เนื่องไม่ได้ใช้ในโฟลว์:
   
    ![กำหนดค่าการ์ดอีเมล](./media/apply-to-each/foreach-5.png)
   
   > [!NOTE]
   > ที่ผ่านมา คุณได้สร้างโฟลว์ง่าย ๆ ที่รับบางอีเมลจากกล่องขาเข้าของคุณ อีเมลเหล่านี้จะถูกส่งกลับในรูปอาร์เรย์ การดำเนินการ **นำไปใช้ในแต่ละอัน** ต้องการอาร์เรย์ ดังนั้นนี่คือสิ่งที่ตรงกับความต้องการ
   > 
   > 

## <a name="add-actions-and-conditions"></a>เพิ่มการดำเนินการและเงื่อนไข
1. เลือก **+ ขั้นตอนใหม่**, **เพิ่มเติม** แล้วเลือกการดำเนินการ **เพิ่ม apply to each**:
   
    ![เลือก apply to each](./media/apply-to-each/foreach-6.png)
2. แทรกโทเค็น**เนื้อความ** ลงในกล่อง**เลือกข้อมูลขาออกจากขั้นตอนก่อนหน้า** บนการ์ด**นำไปใช้ในแต่ละอัน** ซึ่งจะดึงเนื้อความของอีเมลที่จะใช้ในการดำเนินการ **นำไปใช้ในแต่ละอัน**:
   
    ![เพิ่มโทเค็นเนื้อความ](./media/apply-to-each/foreach-7.png)
3. เลือก**เพิ่มเงื่อนไข**:
   
    ![เพิ่มเงื่อนไข](./media/apply-to-each/foreach-8.png)
4. กำหนดค่าการ์ด**เงื่อนไข** เพื่อค้นหาชื่อเรื่องของแต่ละอีเมลสำหรับคำว่า "meet now":
   
   * แทรกโทเค็น**เรื่อง**ลงในกล่อง**ชื่อวัตถุ**
   * เลือก**ประกอบด้วย** ในรายการ**ความสัมพันธ์**
   * ป้อน **meet now** ลงในกล่อง**ค่า**
     
     ![กำหนดค่าเงื่อนไข](./media/apply-to-each/foreach-subject-condition.png)
5. เลือก**เพิ่มเติม** แล้วเลือก**เพิ่มเงื่อนไข**จากสาขา**ถ้าใช่ ไม่ต้องทำอะไร** ซึ่งจะเปิดการ์ด**เงื่อนไข 2** ให้กำหนดค่าการ์ดดังนี้:
   
   * แทรกโทเค็น**ความสำคัญ**ลงในกล่อง**ชื่อวัตถุ**
   * เลือก**เท่ากับ**ในรายการ**ความสัมพันธ์**
   * ป้อน**สูง**ลงในกล่อง**ค่า**
     
     ![เพิ่มเงื่อนไข](./media/apply-to-each/foreach-importance-condition.png)
6. เลือก**เพิ่มการดำเนินการ** ภายใต้ส่วน**ถ้าใช่ ไม่ต้องทำอะไร** ซึ่งจะเปิดการ์ด**เลือกการดำเนินการ** ซึ่งคุณจะกำหนดสิ่งที่จะเกิดขึ้นถ้าเงื่อนไขการค้นหา (อีเมล **meet now** ที่ถูกส่งโดยมีความสำคัญสูง) เป็นจริง:
   
    ![เพิ่มการดำเนินการ](./media/apply-to-each/foreach-9.png)
7. ค้นหา**การแจ้งเตือน** แล้วเลือกการดำเนินการ **การแจ้งเตือน - Send me a mobile notification**:
   
    ![ค้นหาและเลือกการแจ้งเตือน](./media/apply-to-each/foreach-10.png)
8. บนการ์ด **Send me a mobile notification** แจ้งรายละเอียดสำหรับการแจ้งเตือนที่จะถูกส่งถ้าชื่อเรื่องของอีเมลที่ประกอบด้วย "meet now" จากนั้น**เพิ่มการดำเนินการ**:
   
    ![กำหนดค่าการแจ้งเตือน](./media/apply-to-each/foreach-11.png)
9. ป้อน**อ่าน**เป็นตัวค้นหา แล้วเลือกการดำเนินการ **Office 365 Outlook - ทำเครื่องหมายว่าอ่านแล้ว** ซึ่งจะทำเครื่องหมายแต่ละอีเมลว่าอ่านแล้ว หลังจากส่งการแจ้งเตือนแบบพุช:
   
    ![เพิ่มการดำเนินการทำเครื่องหมายว่าอ่านแล้ว](./media/apply-to-each/foreach-12.png)
10. เพิ่มโทเค็น **Id ข้อความ** ในกล่อง **Id ข้อความ**ของการ์ด**ทำเครื่องหมายว่าอ่านแล้ว** คุณอาจจำเป็นต้องเลือก**ดูเพิ่มเติม** เพื่อค้นหาโทเค็น **Id ข้อความ** ซึ่งระบุ Id ของข้อความที่จะถูกทำเครื่องหมายว่าอ่านแล้ว:
    
     ![เพิ่ม id ข้อความ](./media/apply-to-each/foreach-13.png)
11. กลับไปที่การ์ด**เงื่อนไข 2** บนสาขา**ถ้าไม่ใช่ ไม่ต้องทำอะไร**:
    
    * เลือก**เพิ่มการดำเนินการ** แล้วพิมพ์**รับผู้จัดการ**ลงในกล่องค้นหา
    * เลือกรายการ **ผู้ใช้ Office 365 - รับผู้จัดการ** จากผลลัพธ์จากการค้นหา
    * ใส่ที่อยู่อีเมล*เต็ม*ของคุณลงในกล่อง**ผู้ใช้**ของการ์ด**รับผู้จัดการ**
      
      ![เพิ่มและกำหนดค่าการดำเนินการรับผู้จัดการ](./media/apply-to-each/foreach-get-manager.png)
12. เลือก**เพิ่มเติม** แล้วเลือก**เพิ่มเงื่อนไข**จากสาขา**ถ้าไม่ใช่** ซึ่งจะเปิดการ์ด**เงื่อนไข 3** กำหนดค่าการ์ดเพื่อตรวจสอบว่า ที่อยู่อีเมลของผู้ส่งอีเมล (โทเค็น จาก) เหมือนกับที่อยู่อีเมลของเจ้านายของคุณ (โทเค็น อีเมล) หรือไม่:
    
    * แทรกโทเค็น**จาก** ลงในกล่อง**ชื่อวัตถุ**
    * เลือก**ประกอบด้วย** ในรายการ**ความสัมพันธ์**
    * ป้อนโทเค็น**อีเมล**ลงในกล่อง**ค่า**
      
      ![กำหนดค่าเงื่อนไขการค้นหา](./media/apply-to-each/foreach-condition3-card.png)
13. เลือก**เพิ่มการดำเนินการ** ภายใต้ส่วน**ถ้าใช่ ไม่ต้องทำอะไร** ของการ์ด**เงื่อนไข 3** ซึ่งจะเปิดตัวการ์ด**ถ้าใช่** ซึ่งคุณจะกำหนดว่าเกิดอะไรขึ้นถ้าเงื่อนไขการค้นหา (อีเมลที่ถูกส่งมาจากเจ้านายของคุณ) เป็นจริง:
    
     ![กำหนดค่าเงื่อนไข](./media/apply-to-each/foreah-condition3-add-action.png)
14. ค้นหา**การแจ้งเตือน** แล้วเลือกการดำเนินการ **การแจ้งเตือน - Send me a mobile notification**:
    
     ![ค้นหาสำหรับการดำเนินการแจ้งเตือน](./media/apply-to-each/foreach-10.png)
15. บนการ์ด **Send me a mobile notification 2** ใส่รายละเอียดสำหรับการแจ้งเตือนที่จะถูกส่งถ้าอีเมลที่มาจากเจ้านายของคุณ จากนั้นเลือก**เพิ่มการดำเนินการ**:
    
     ![กำหนดค่าการ์ดการแจ้งเตือน](./media/apply-to-each/foreach-boss-notification.png)
16. เพิ่มการดำเนินการ**Office 365 Outlook - ทำเครื่องหมายว่าอ่านแล้ว** ซึ่งจะทำเครื่องหมายแต่ละอีเมลว่าอ่านแล้ว หลังจากส่งการแจ้งเตือนแบบพุช:
    
     ![เพิ่มการดำเนินการทำเครื่องหมายว่าอ่านแล้ว](./media/apply-to-each/foreach-12.png)
17. เพิ่มโทเค็น **Id ข้อความ** ลงในการ์ด**ทำเครื่องหมายว่าอ่านแล้ว 2** คุณอาจจำเป็นต้องเลือก**ดูเพิ่มเติม** เพื่อค้นหาโทเค็น **Id ข้อความ** ซึ่งระบุ Id ของข้อความที่จะถูกทำเครื่องหมายว่าอ่านแล้ว:
    
     ![กำหนดค่าการดำเนินการทำเครื่องหมายว่าอ่านแล้ว](./media/apply-to-each/foreach-mark-as-read2.png)
18. ตั้งชื่อโฟลว์ของคุณ และจากนั้นสร้าง:
    
     ![ตั้งชื่อให้โฟลว์ของคุณ และบันทึก](./media/apply-to-each/foreach-14.png)

ถ้าคุณทำตาม โฟลว์ของคุณควรมีลักษณะคล้ายกับไดอะแกรมนี้:

![ภาพรวมของโฟลว์ที่ถูกสร้าง](./media/apply-to-each/foreach-flow-finished.png)

## <a name="run-the-flow"></a>เรียกใช้โฟลว์
1. ส่งอีเมลที่มีความสำคัญสูงให้ตัวคุณเอง ที่ประกอบด้วย **meet now** ในชื่อเรื่อง (หรือให้บุคคลอื่นในองค์กรของคุณส่งอีเมลดังกล่าวให้)
2. ยืนยันว่าอีเมลอยู่ในกล่องขาเข้าของคุณแล้วแต่ยังไม่ได้อ่าน
3. ลงชื่อเข้าใช้ Microsoft Flow เลือก**โฟลว์ของฉัน** แล้วเลือก**เรียกใช้ทันที**:
   
    ![เรียกใช้ทันที](./media/apply-to-each/foreach-run-1.png)
4. เลือก**เรียกใช้โฟลว์** เพื่อยืนยันว่าคุณต้องการเรียกใช้โฟลว์จริง ๆ:
   
    ![ยืนยันการเรียกใช้](./media/apply-to-each/foreach-run-2.png)
5. หลังจากสักครู่ คุณจะเห็นผลลัพธ์ของการเรียกใช้เสร็จเรียบร้อยแล้ว:
   
    ![ผลลัพธ์การเรียกใช้](./media/apply-to-each/foreach-run-3.png)

## <a name="view-results-of-the-run"></a>ดูผลลัพธ์ของการทำงาน
ตอนนี้คุณได้เรียกใช้โฟลว์สำเร็จแล้ว คุณควรได้รับการแจ้งเตือนแบบพุชบนอุปกรณ์เคลื่อนที่ของคุณ

1. เปิดแอป Microsoft Flow บนอุปกรณ์เคลื่อนที่ จากนั้นในแท็บ**กิจกรรม** คุณจะเห็นการแจ้งเตือนแบบพุชเกี่ยวกับการประชุม:
   
    ![เลือกแท็บกิจกรรม](./media/apply-to-each/foreach-notification-1.png)
2. เพื่อดูเนื้อหาแบบเต็มของการแจ้งเตือน คุณอาจต้องเลือกการแจ้งเตือน คุณจะเห็นการแจ้งเตือนแบบเต็มรูปแบบ ดังนี้:
   
    ![รายละเอียดการแจ้งเตือน](./media/apply-to-each/foreach-notification-2.png)
   
   > [!NOTE]
   > ถ้าคุณไม่ได้รับการแจ้งเตือนแบบพุช ยืนยันว่าอุปกรณ์เคลื่อนที่ของคุณมีการเชื่อมต่อข้อมูล
   > 
   > 
