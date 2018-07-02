## <a name="what-is-an-environment"></a>สภาพแวดล้อมคืออะไร:
สภาพแวดล้อมคือ พื้นที่เสมือนที่ใช้ในการจัดเก็บ จัดการ และแชร์แอป โฟลว์ และข้อมูลทางธุรกิจใน Common Data Service สภาพแวดล้อมแยกตามตำแหน่งที่ตั้งทางภูมิศาสตร์ ดังนั้น แอปและข้อมูลทั้งหมดที่เก็บอยู่ภายในฐานข้อมูลของสภาพแวดล้อมจะแยกตามตำแหน่งที่ตั้งทางภูมิศาสตร์ด้วย  

## <a name="terms-you-should-get-familiar-with"></a>เงื่อนไขที่คุณควรทำความคุ้นเคย

| **เงื่อนไข** | **คำอธิบาย** |
| --- | --- |
| **ศูนย์การจัดการ** |ศูนย์การจัดการคือ [พอร์ทัลเว็บ](https://admin.flow.microsoft.com)สำหรับการจัดการสภาพแวดล้อมและนโยบายการป้องกันข้อมูลสูญหายทั้งหมดของคุณ |
| **Common Data Service** |Common Data Service ให้คุณสามารถเพิ่มขีดความสามารถในการเก็บข้อมูลและสร้างแบบจำลองไปยังแอปของคุณ |
| **บทบาทสภาพแวดล้อม** |บทบาทสภาพแวดล้อมทั้งสองคือ ผู้ดูแลระบบสภาพแวดล้อมและผู้สร้างสภาพแวดล้อม |
| **บทบาทผู้ใช้** |บทบาทผู้ใช้ตามค่าเริ่มต้นสองบทบาทคือ ผู้ใช้ในองค์กรและเจ้าของฐานข้อมูล คุณสามารถเพิ่มบทบาทและเชื่อมโยงสิทธิ์การใช้งานกับบทบาทเหล่านั้นได้ |

## <a name="purposes-for-an-environment"></a>วัตถุประสงค์สำหรับสภาพแวดล้อม
คุณสามารถใช้สภาพแวดล้อมเพื่อ:  

* แยกแอป โฟลว์ และข้อมูลทางธุรกิจตามบทบาทต่าง ๆ ข้อกำหนดความปลอดภัย หรือผู้ใช้  
* แยกแอป โฟลว์ และข้อมูลทางธุรกิจตามตำแหน่งที่ตั้งของทีมหรือแผนกของคุณ
* จัดการสภาพแวดล้อมการทดสอบและการผลิต  

## <a name="how-to-use-environments"></a>วิธีใช้สภาพแวดล้อม
สภาพแวดล้อมสามารถทำงานสำหรับหลายวัตถุประสงค์ได้ โดยขึ้นอยู่กับความต้องการขององค์กรของคุณ ตัวอย่างเช่น:  

* คุณสามารถเลือกที่จะสร้างแอปและโฟลว์ทั้งหมดของคุณในสภาพแวดล้อมเดียวได้ 
* คุณสามารถเลือกที่จะสร้างสภาพแวดล้อมสำหรับแอปและโฟลว์ชนิดต่าง ๆ ได้ ตัวอย่างเช่น คุณสามารถสร้างสภาพแวดล้อมสำหรับการทดสอบและสภาพแวดล้อมอื่นสำหรับการผลิตได้  
* นอกจากนี้ คุณอาจเลือกที่จะสร้างสภาพแวดล้อมตามโครงสร้างองค์กรของคุณ หรือตามตำแหน่งที่ตั้งทางภูมิศาสตร์ของทีมหรือแผนกของคุณ ตัวอย่างเช่น ถ้าคุณมีทีมงานในออสเตรเลีย เม็กซิโก และยุโรป คุณสามารถสร้างสภาพแวดล้อมสำหรับแต่ละตำแหน่งที่ตั้งเหล่านี้ ได้ และจัดการสภาพแวดล้อมแยกกัน  

**หมายเหตุ**: ผู้ใช้จะมองไม่เห็นสภาพแวดล้อม ดังนั้น พวกเขาไม่จำเป็นต้องกังวลว่าตนอยู่ในสภาพแวดล้อมใด สภาพแวดล้อมเป็นเครื่องมือสำหรับผู้ดูแลระบบในการจัดประเภท จัดการ รวมถึงแชร์แอปและโฟลว์ของงองค์กร  

## <a name="what-are-roles"></a>บทบาทคืออะไร?
บุคคลที่สามารถเข้าใช้งานสภาพแวดล้อมได้ต้องได้รับกำหนดให้มีบทบาทใดบทบาทหนึ่ง นั่นคือ **ผู้ดูแลระบบสภาพแวดล้อม**หรือ**ผู้สร้างสภาพแวดล้อม** ผู้ดูแลสภาพแวดล้อมสามารถทำงานทั้งหมดในการดูและระบบในสภาพแวดล้อมหนึ่ง ๆ ผู้สร้างสภาพแวดล้อมสามารถสร้างทรัพยากรในสภาพแวดล้อมที่มีอยู่ได้ บุคคลหนึ่งสามารถมีทั้งสองบทบาทพร้อมกันได้  

**หมายเหตุ**: ผู้ใช้ทั้งหมดจะสามารถเข้าถึงสภาพแวดล้อมค่าเริ่มต้นได้เมื่อผู้ใช้แต่ละรายได้รับสิทธิ์การเข้าถึง Microsoft Flow ผู้ใช้สามารถเข้าถึงหลายสภาพแวดล้อมได้  

## <a name="create-an-environment"></a>สร้างสภาพแวดล้อม
คุณสร้างสภาพแวดล้อมจาก [ศูนย์การจัดการ Microsoft Flow](https://admin.flow.microsoft.com)ด้วยขั้นตอนเหล่านี้:  

1. ตั้งชื่อสภาพแวดล้อมของคุณ
2. เลือกภูมิภาคที่จะโฮสต์สภาพแวดล้อมของคุณ
3. นอกจากนี้ คุณสามารถตัดสินใจที่จะสร้างฐานข้อมูลสำหรับสภาพแวดล้อมของคุณได้ คุณสามารถสร้างฐานข้อมูลหลังจากที่คุณสร้างสภาพแวดล้อมได้ ถ้าคุณต้องการ
4. อีกทางหนึ่งคือ เลือกว่าใครจะสามารถเข้าถึงฐานข้อมูลได้ คุณสามารถจำกัดการเข้าถึง หรืออนุญาตให้ทุกคนเข้าถึงฐานข้อมูลได้ 

## <a name="add-users-to-an-environment"></a>เพิ่มผู้ใช้ไปยังสภาพแวดล้อม
หลังจากที่คุณสร้างสภาพแวดล้อม คุณสามารถเพิ่มผู้ใช้โดยกำหนดบทบาทเป็นผู้ดูแลระบบสภาพแวดล้อม หรือบทบาทผู้สร้างสภาพแวดล้อมได้ เช่นเดียวกับงานการดูแลระบบอื่น ๆ คุณจะทำขั้นตอนนี้จากศูนย์การจัดการ  

หลังจากที่คุณสร้างสภาพแวดล้อมและเพิ่มผู้ใช้แล้ว คุณอาจต้องการสร้างนโยบายการป้องกันข้อมูลสูญหาย (DLP) เพื่อช่วยในการจัดการการใช้ข้อมูลธุรกิจของคุณ เราจะกล่าวถึงในหัวข้อถัดไป 
