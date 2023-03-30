### วิธีทำ Download File ใน Vue 2

## ทำการสร้าง function เก็บไว้ใน methods ตามตัวอย่างด้านล่าง
```
methods: {
  // สร้าง Function ขึ้นมา 1 ตัว โดยรับ parameter มา 2 ตัว
  // 1.text คือ ข้อความที่อยู่ใน file ที่จะดาวน์โหลดออกมา
  // 2.fileName ชื่อไฟล์จะต้องมีนามสกุลไฟล์ด้วย เช่น .txt
    downloadFile(text, fileName){
      const blob = new Blob([text], {type: "text/plain"}); // สร้าง Blob object ขึ้นมา พร้อมระบุชนิด type เป็น text/plain
      const url = window.URL.createObjectURL(blob); // สร้าง links 
      const a = document.createElement("a"); // สร้าง tag a 
      a.href = url; // กำหนด href ให้ tag a ที่สร้างมาจากด้านบน
      a.download = filename;
      a.click();
  }
}
```

## วิธีการเรียกใช้งาน

สร้างมานำ function downloadFile ไปใช้ได้เลย เช่น เรามี methods สำหรับดาวน์โหลดข้อมูลผู้ใช้ อาจจะตั้งชื่อ function ว่า dowloadFileUser 
หากต้องการให้ dowloadFileUser ทำงาน ให้นำ dowloadFileUser ไปผูกไว้กับปุ่มโดยใช้ @click

```
methods: {
  dowloadFileUser () {
    const txt = "Firstname and Lastname"
    // โยน txt เข้า arguments ตัวแรก และตัวที่สองคือ ชื่อไฟล์ พร้อมนาม สกุล
    this.downloadFile(txt, 'user.txt')
  }
}

```

## โค้ดตัวอย่างเมื่อเอามารวมกัน
```
methods: {
    downloadFile(text, fileName){
      const blob = new Blob([text], {type: "text/plain"});
      const url = window.URL.createObjectURL(blob);
      const a = document.createElement("a");
      a.href = url;
      a.download = filename;
      a.click();
  },
  dowloadFileUser () {
    const txt = "Firstname and Lastname"
    this.downloadFile(txt, user.txt)
  }
}
```

## ตัวอย่างผลลัพธ์
<img width="680" alt="image" src="https://user-images.githubusercontent.com/79618937/228761137-6168cb62-d23b-401d-8d3d-aebf9373a3ae.png">

