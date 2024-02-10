# INTERPRETER

Interpreter คือการแปลคำสั่งหนึ่งของsource code เป็นmachine code ซึ่งจะถูกดำเนินการโดยตัวประมวลผลภาษาและทำงานทันทีก่อนที่จะเคลื่อนไปยังบรรทัดถัดไป, 
หากมีข้อผิดพลาดในคำสั่ง Interpreterจะสิ้นสุดการแปลที่คำสั่งนั้นและแสดงerrorในคำสั่งนั้น Interpreterจะไปยังที่บรรทัดถัดไปเพื่อทำงานก็ต่อเมื่อerror ถูกแก้ไข, 
Interpreterจะดำเนินการคำสั่งที่เขียนในภาษาโปรแกรมหรือสคริปต์โดยตรงโดยไม่ต้องแปลงไปเป็น object code หรือ machine code ก่อน, Interpreter จะแปลทีละบรรทัดแล้วค่อยดำเนินการ<br>
ตัวอย่าง:Perl, Python and Matlab.

<img src="https://media.geeksforgeeks.org/wp-content/uploads/20210617144008/interpreter.png"  width='720' height='300'>

## ความแตกต่างระหว่าง Compiler และ Interpreter

**Compiler**
<ul>
<li>เป็นโปรแกรมที่แปลงsource codeทั้งหมดเป็นmachine codeที่สามารถดำเนินการได้สำหรับ CPU</li>
<li>ใช้เวลามากในการวิเคราะห์source codeทั้งหมด แต่เวลาดำเนินการโดยรวมของโปรแกรมจะเร็วกว่าเมื่อเปรียบเทียบกับ Interpreter</li>
<li>สร้างข้อความ error หลังจากสแกนโปรแกรมทั้งหมดเท่านั้น การ debug จึงมีความยากเนื่องจากerrorสามารถอยู่ที่บรรทัดไหนก็ได้ในโปรแกรม</li>
<li>ต้องการหน่วยความจำมากสำหรับการสร้าง object code</li>
<li>สร้าง intermediate object code</li>
<li>เหมาะสำหรับวัตถุประสงค์ด้านความปลอดภัยมากกว่า</li>
</ul>

**Interpreter**
<ul>
<li>รับsource codeและเรียกใช้มันทีละบรรทัดโดยแปลแต่ละบรรทัดเมื่อมาถึง</li>
<li>ใช้เวลาน้อยกว่าในการวิเคราะห์source code แต่เวลาดำเนินการโดยรวมของโปรแกรมจะช้ากว่า</li>
<li>การ debug ง่ายกว่า เนื่องจากเป็นการแปลโปรแกรมไปเรื่อยไปจนกว่าจะพบ error</li>
<li>ต้องการหน่วยความจำน้อยกว่า Compiler เนื่องจาก object code</li>
<li>ไม่มีการสร้าง intermediate object code</li>
<li>มีความเสี่ยงน้อยเล็กน้อยในส่วนของความปลอดภัย</li>
</ul>

## ความจำเป็นของ Interpreter

ความจำเป็นแรกและสำคัญของInterpreter คือการแปลsource code จากภาษาระดับสูงเป็นภาษาเครื่อง และถึงแม้เราจะมีCompiler ให้บริการในวัตถุประสงค์นี้อยู่แล้วCompiler 
ก็ยังมีข้อเสียหลายประการ เช่น หาก source code มีขนาดใหญ่มาก อาจต้องใช้เวลาหลายชั่วโมงในการ Compile source code ซึ่งจะเพิ่มระยะเวลาในการ Compile เป็นอย่างมาก, 
จึงเป็นส่วนที่ Interpreter จะเข้ามาช่วยได้, โดย Interpreter สามารถลดระยะเวลา Compile ได้เป็นอย่างมาก เนื่องจากถูกออกแบบให้แปลคำสั่งเดียวทีละคำสั่งและดำเนินการโดยทันที 
ดังนั้น แทนที่จะรอ code ทั้งหมด Interpreter จะแปลบรรทัดเดียวและดำเนินการโดยทันที

## 4 ประเภทของ Interpreter 

<ol>
<li>Bytecode Interpreter<br>
ความต้องการของการแปล Bytecode และคอมไพล์แบบ just-in-time ทำให้ความแตกต่างระหว่าง Compiler และ Interpreter 
น้อยลง, Bytecode Interpreter สามารถประมวลผลได้ถึง 256 คำสั่ง โดยแต่ละคำสั่งจะเริ่มต้นด้วยByte
</li>

<li>Threaded Code Interpreter<br>
Interpreter นี้จะใช้ตัว pointer แทนไบต์ ไม่เหมือนกับ Bytecode Interpreter, แต่ละคำสั่งเป็นคำสั่งที่ชี้ไปยังฟังก์ชันหรือลำดับคำสั่ง อาจตามด้วย parameter,
จำนวนของคำสั่งที่แตกต่างกันจะถูกจำกัดโดยหน่วยความจำและพื้นที่แอดเดรสที่พร้อมใช้งาน
</li>

<li>Abstract Syntax Tree Interpreter<br>
หากคุณเป็นนักพัฒนา TypeScript และมีความคุ้นเคยบางส่วนกับโครงสร้างของ TypeScript คุณอาจได้ยินเกี่ยวกับ Abstract Syntax Tree (AST) 
ซึ่งเป็นวิธีในการแปลงsource codeเป็นต้นไม้รูปโครงที่ถูกปรับปรุง แล้วดำเนินการโปรแกรมตามโครงสร้างต้นไม้นี้ หรือใช้ในการสร้างmachine codeที่เป็นธรรมชาติแบบ just-in-time<br>
อย่างไรก็ตามสำหรับ Interpreter การใช้ AST จะทำให้มีความต้องการด้านประสิทธิภาพมากขึ้น, Interpreter ที่ต้องเดินทางใน AST จึงช้ากว่าตัวแปลที่สร้าง Bytecode
</li>

<li>Just-in-Time Compilation<br>
เป็นเทคนิคที่ซึ่งการแสดงผลตัวแทนกลางจะถูกคอมไพล์เป็นรหัสเครื่องธรรมดาที่เวลารันไทม์
</li>
</ol>

Reference
<ul>
<li>https://www.geeksforgeeks.org/language-processors-assembler-compiler-and-interpreter/</li>
<li>https://www.geeksforgeeks.org/introduction-to-interpreters/</li>
<li>https://builtin.com/software-engineering-perspectives/compiler-vs-interpreter</li>
</ul>
