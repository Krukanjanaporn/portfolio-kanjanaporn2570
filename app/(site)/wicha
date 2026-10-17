import os, zipfile, textwrap

base = "/mnt/data/บทเรียนออนไลน์_GitHub"
os.makedirs(base, exist_ok=True)

files = {}

files["index.html"] = r'''<!DOCTYPE html>
<html lang="th">
<head>
<meta charset="UTF-8">
<meta name="viewport" content="width=device-width, initial-scale=1">
<meta name="description" content="เว็บไซต์บทเรียนออนไลน์ แยกตามรายวิชา">
<title>ห้องเรียนออนไลน์ | เลือกรายวิชา</title>
<style>
:root{--ink:#172554;--blue:#2563eb;--sky:#eff6ff;--line:#dbeafe;--green:#047857}
*{box-sizing:border-box}body{margin:0;font-family:Tahoma,"Noto Sans Thai",sans-serif;color:#1f2937;background:#f8fafc;line-height:1.7}
header{background:linear-gradient(135deg,#1d4ed8,#0f766e);color:white;padding:48px 20px;text-align:center}
header h1{margin:0 0 8px;font-size:clamp(1.6rem,4vw,2.5rem)}header p{margin:0}
main{max-width:1050px;margin:30px auto;padding:0 18px}.grid{display:grid;grid-template-columns:repeat(auto-fit,minmax(240px,1fr));gap:18px}
.card{background:white;border:1px solid var(--line);border-radius:18px;padding:24px;box-shadow:0 8px 24px #0f172a0b}
.card h2{margin-top:0;color:var(--ink)}.card a,.btn{display:inline-block;background:var(--blue);color:white;text-decoration:none;padding:10px 16px;border-radius:10px;font-weight:bold}
.card a:hover,.btn:hover{filter:brightness(.92)}.note{background:#ecfdf5;border-left:4px solid #10b981;padding:14px 18px;border-radius:8px;margin:24px 0}
footer{text-align:center;color:#64748b;padding:28px}
</style>
</head>
<body>
<header><h1>ห้องเรียนออนไลน์</h1><p>เรียนรู้ได้ทุกที่ • เนื้อหาบทเรียน • สื่อการสอน • แบบทดสอบก่อนเรียนและหลังเรียน</p></header>
<main>
<div class="note"><strong>วิธีใช้:</strong> เลือกรายวิชาด้านล่าง จากนั้นเปิดบทเรียน อ่านเนื้อหา และทำแบบทดสอบก่อนเรียน/หลังเรียน เว็บไซต์นี้เป็นไฟล์ HTML ไม่ต้องติดตั้งระบบฐานข้อมูล</div>
<section class="grid">
<article class="card"><h2>💻 วิทยาการคำนวณ</h2><p>แนวคิดเชิงคำนวณ การแก้ปัญหา อัลกอริทึม และการเขียนโปรแกรมเบื้องต้น</p><a href="วิทยาการคำนวณ/index.html">เข้าสู่รายวิชา</a></article>
<article class="card"><h2>🖥️ วิชาคอมพิวเตอร์</h2><p>ส่วนประกอบคอมพิวเตอร์ การจัดการไฟล์ อินเทอร์เน็ต และความปลอดภัยดิจิทัล</p><a href="คอมพิวเตอร์/index.html">เข้าสู่รายวิชา</a></article>
<article class="card"><h2>🧰 การงานอาชีพ</h2><p>ทักษะการทำงาน การวางแผนงาน อาชีพ และการใช้ทรัพยากรอย่างคุ้มค่า</p><a href="การงานอาชีพ/index.html">เข้าสู่รายวิชา</a></article>
</section>
<div class="note"><strong>สำหรับครู:</strong> สามารถแก้ไขข้อความและคำถามได้ในไฟล์ <code>index.html</code> ของแต่ละรายวิชา เปิดไฟล์ด้วยโปรแกรมแก้ไขข้อความ เช่น VS Code แล้วบันทึกเป็น UTF-8</div>
</main><footer>ห้องเรียนออนไลน์ • สร้างด้วย HTML, CSS และ JavaScript</footer>
</body></html>'''

subjects = [
("วิทยาการคำนวณ","💻","เรียนรู้การคิดอย่างเป็นระบบ การแยกปัญหาเป็นส่วนย่อย การออกแบบขั้นตอนวิธี และการเขียนโปรแกรมเบื้องต้น",
 [
 ("แนวคิดเชิงคำนวณ","แนวคิดเชิงคำนวณ คือกระบวนการคิดเพื่อแก้ปัญหาอย่างเป็นขั้นตอน ไม่จำเป็นต้องใช้คอมพิวเตอร์ทุกครั้ง","องค์ประกอบสำคัญ ได้แก่ การแยกย่อยปัญหา การหารูปแบบ การคิดเชิงนามธรรม และการออกแบบอัลกอริทึม"),
 ("อัลกอริทึมและผังงาน","อัลกอริทึม คือชุดขั้นตอนที่ชัดเจนสำหรับแก้ปัญหาหรือทำงานให้สำเร็จ","ผังงานใช้สัญลักษณ์แสดงลำดับงาน เช่น วงรีแทนเริ่มต้น/สิ้นสุด สี่เหลี่ยมผืนผ้าแทนกระบวนการ และสี่เหลี่ยมขนมเปียกปูนแทนการตัดสินใจ"),
 ("การเขียนโปรแกรมเบื้องต้น","โปรแกรมคือชุดคำสั่งที่คอมพิวเตอร์ทำตาม การเขียนโปรแกรมที่ดีควรอ่านง่าย ทดสอบได้ และแก้ไขได้","ลำดับคำสั่ง การทำซ้ำ และเงื่อนไข เป็นโครงสร้างพื้นฐานที่พบได้ในภาษาโปรแกรมหลายภาษา")
 ],
 [
 ("แนวคิดเชิงคำนวณช่วยให้ทำสิ่งใด","แก้ปัญหาอย่างเป็นระบบ","ทำให้จอภาพสว่างขึ้น","เพิ่มความเร็วอินเทอร์เน็ต","เปลี่ยนสีคีย์บอร์ด",0),
 ("สัญลักษณ์ใดมักใช้แทนการตัดสินใจในผังงาน","วงรี","สี่เหลี่ยมขนมเปียกปูน","สี่เหลี่ยมผืนผ้า","ลูกศร",1),
 ("โครงสร้างใดใช้ทำคำสั่งเดิมซ้ำหลายครั้ง","การทำซ้ำ","การปิดเครื่อง","การจัดรูปแบบเอกสาร","การลบไฟล์",0),
 ("อัลกอริทึมควรมีลำดับขั้นตอนชัดเจน","จริง","เท็จ","", "",0)
 ]),
("คอมพิวเตอร์","🖥️","ทำความรู้จักฮาร์ดแวร์ ซอฟต์แวร์ การจัดการไฟล์ การใช้อินเทอร์เน็ต และการดูแลความปลอดภัย",
 [
 ("ฮาร์ดแวร์และซอฟต์แวร์","ฮาร์ดแวร์คืออุปกรณ์ที่จับต้องได้ เช่น จอภาพ เมาส์ และแป้นพิมพ์ ส่วนซอฟต์แวร์คือโปรแกรมหรือชุดคำสั่ง","คอมพิวเตอร์ทำงานร่วมกันระหว่างฮาร์ดแวร์และซอฟต์แวร์ เพื่อรับข้อมูล ประมวลผล จัดเก็บ และแสดงผล"),
 ("การจัดการไฟล์","ไฟล์เก็บข้อมูล เช่น เอกสาร รูปภาพ และวิดีโอ ส่วนโฟลเดอร์ใช้จัดกลุ่มไฟล์ให้ค้นหาได้ง่าย","ตั้งชื่อไฟล์ให้สื่อความหมาย จัดเก็บไว้ในโฟลเดอร์ที่เหมาะสม และสำรองข้อมูลสำคัญเป็นประจำ"),
 ("ความปลอดภัยดิจิทัล","ข้อมูลส่วนตัว เช่น รหัสผ่าน ที่อยู่ และหมายเลขโทรศัพท์ ควรเปิดเผยอย่างระมัดระวัง","ใช้รหัสผ่านที่คาดเดายาก ไม่ส่งรหัสผ่านให้ผู้อื่น ระวังลิงก์น่าสงสัย และออกจากระบบเมื่อใช้เครื่องสาธารณะ")
 ],
 [
 ("ข้อใดเป็นฮาร์ดแวร์","โปรแกรมวาดภาพ","เมาส์","ระบบปฏิบัติการ","เว็บเบราว์เซอร์",1),
 ("โฟลเดอร์มีประโยชน์หลักอย่างไร","ช่วยจัดกลุ่มไฟล์","ทำให้จอภาพใหญ่ขึ้น","เพิ่มหน่วยความจำทันที","ป้องกันไฟดับ",0),
 ("เมื่อได้รับลิงก์ที่น่าสงสัยควรทำอย่างไร","รีบกดทันที","ส่งต่อให้ทุกคน","ตรวจสอบก่อนและไม่เปิดหากไม่น่าเชื่อถือ","กรอกรหัสผ่านเพื่อทดสอบ",2),
 ("ควรเปิดเผยรหัสผ่านให้เพื่อนเพื่อความสะดวก","จริง","เท็จ","", "",1)
 ]),
("การงานอาชีพ","🧰","ฝึกวางแผนงาน ทำงานร่วมกัน ใช้ทรัพยากรอย่างคุ้มค่า และสำรวจแนวทางอาชีพ",
 [
 ("กระบวนการทำงาน","การทำงานอย่างมีประสิทธิภาพเริ่มจากการวางแผน กำหนดเป้าหมาย แบ่งหน้าที่ ลงมือทำ และประเมินผล","การกำหนดเวลาและอุปกรณ์ที่ต้องใช้ช่วยลดความผิดพลาด ควรทบทวนผลและปรับปรุงเมื่อพบปัญหา"),
 ("การทำงานเป็นทีม","ทีมที่ดีสื่อสารอย่างสุภาพ รับฟังความคิดเห็น แบ่งหน้าที่ชัดเจน และรับผิดชอบงานของตน","หากมีความเห็นต่าง ควรอธิบายเหตุผล รับฟังกัน และร่วมกันเลือกแนวทางที่เหมาะสม"),
 ("การใช้ทรัพยากรอย่างคุ้มค่า","การใช้ทรัพยากรอย่างประหยัดช่วยลดค่าใช้จ่ายและลดผลกระทบต่อสิ่งแวดล้อม","วางแผนก่อนซื้อ ใช้วัสดุให้เหมาะสม นำของกลับมาใช้ซ้ำเมื่อปลอดภัย และแยกขยะตามประเภท")
 ],
 [
 ("ขั้นตอนใดควรทำก่อนลงมือทำงาน","วางแผน","ประเมินผลทันที","เก็บอุปกรณ์","ส่งงาน",0),
 ("ทีมทำงานที่ดีควรมีลักษณะใด","ไม่แบ่งหน้าที่","สื่อสารและรับผิดชอบร่วมกัน","ไม่รับฟังความเห็น","ทำงานโดยไม่มีเป้าหมาย",1),
 ("ข้อใดช่วยใช้ทรัพยากรอย่างคุ้มค่า","ซื้อของเกินจำเป็น","ทิ้งของที่ยังใช้ได้","วางแผนการใช้วัสดุและนำกลับมาใช้ซ้ำเมื่อเหมาะสม","เปิดไฟทิ้งไว้",2),
 ("การประเมินผลช่วยให้เห็นสิ่งที่ควรปรับปรุง","จริง","เท็จ","", "",0)
 ])
]

def esc(s):
    return s.replace("&","&amp;").replace("<","&lt;").replace(">","&gt;")

for name, emoji, intro, lessons, quiz in subjects:
    folder = os.path.join(base, name)
    os.makedirs(folder, exist_ok=True)
    lesson_html = ""
    for i,(title,desc,detail) in enumerate(lessons,1):
        lesson_html += f'''<article class="lesson"><h3>บทที่ {i}: {esc(title)}</h3><p>{esc(desc)}</p><div class="detail"><strong>สรุปเนื้อหา</strong><p>{esc(detail)}</p></div><label>เพิ่มสื่อการสอน (ถ้ามี):</label><p class="muted">ครูสามารถใส่ลิงก์วิดีโอ ใบงาน หรือไฟล์ประกอบในส่วนนี้ได้</p></article>'''
    questions = []
    for i,q in enumerate(quiz,1):
        question,a,b,c,d,correct = q
        if a in ("จริง","เท็จ") and b in ("เท็จ","จริง"):
            opts = [("จริง",0),("เท็จ",1)]
        else:
            opts = [(a,0),(b,1),(c,2),(d,3)]
        questions.append({"q":question,"opts":opts,"correct":correct})
    import json
    qjson = json.dumps(questions, ensure_ascii=False)
    html = f'''<!DOCTYPE html>
<html lang="th"><head><meta charset="UTF-8"><meta name="viewport" content="width=device-width, initial-scale=1">
<meta name="description" content="{esc(intro)}"><title>{esc(name)} | ห้องเรียนออนไลน์</title>
<style>
:root{{--blue:#1d4ed8;--dark:#172554;--light:#eff6ff;--line:#dbeafe;--green:#047857}}
*{{box-sizing:border-box}}body{{margin:0;background:#f8fafc;color:#1f2937;font-family:Tahoma,"Noto Sans Thai",sans-serif;line-height:1.75}}
header{{padding:34px 18px;background:linear-gradient(135deg,#1d4ed8,#0f766e);color:white}}header .inner,main{{max-width:900px;margin:auto}}header h1{{margin:0;font-size:clamp(1.6rem,4vw,2.3rem)}}header p{{margin:6px 0 16px}}
a{{color:#1d4ed8}}.back{{color:white}}main{{padding:22px 16px}}nav{{display:flex;gap:10px;flex-wrap:wrap;margin:0 0 22px}}nav a{{background:white;border:1px solid var(--line);padding:8px 12px;border-radius:10px;text-decoration:none}}
section,.lesson,.quizbox{{background:white;border:1px solid var(--line);border-radius:16px;padding:20px;margin-bottom:18px;box-shadow:0 6px 18px #0f172a08}}
h2{{color:var(--dark);margin-top:0}}h3{{color:#1d4ed8;margin-top:0}}.detail{{background:var(--light);padding:12px 15px;border-radius:10px}}.detail p{{margin-bottom:0}}
button{{border:0;border-radius:10px;background:var(--blue);color:white;padding:10px 16px;font:inherit;cursor:pointer;margin:6px 4px 6px 0}}button.secondary{{background:#475569}}button:hover{{filter:brightness(.93)}}
label.option{{display:block;border:1px solid #e2e8f0;padding:10px 12px;border-radius:10px;margin:8px 0;cursor:pointer}}label.option:hover{{background:#f8fafc}}input{{margin-right:8px}}
.result{{padding:12px;background:#ecfdf5;border-left:4px solid #10b981;border-radius:8px;margin-top:12px}}.muted{{color:#64748b;font-size:.95rem}}.progress{{height:8px;background:#e2e8f0;border-radius:99px;overflow:hidden}}.progress span{{display:block;height:100%;background:#10b981;width:0}}footer{{text-align:center;color:#64748b;padding:20px}}
</style></head><body>
<header><div class="inner"><a class="back" href="../index.html">← กลับหน้าหลัก</a><h1>{emoji} รายวิชา{esc(name)}</h1><p>{esc(intro)}</p><div>เลือกอ่านบทเรียน แล้วทำแบบทดสอบเพื่อทบทวนความเข้าใจ</div></div></header>
<main><nav><a href="#lessons">📘 บทเรียน</a><a href="#pretest">📝 แบบทดสอบก่อนเรียน</a><a href="#posttest">✅ แบบทดสอบหลังเรียน</a></nav>
<section><h2>จุดประสงค์การเรียนรู้</h2><ul><li>อธิบายแนวคิดสำคัญของบทเรียนได้</li><li>นำความรู้ไปประยุกต์ใช้ในสถานการณ์ใกล้ตัว</li><li>ตรวจสอบความเข้าใจของตนเองก่อนและหลังเรียน</li></ul><p class="muted">หมายเหตุ: เนื้อหาเริ่มต้นเป็นตัวอย่าง ครูสามารถแก้ไขให้ตรงกับระดับชั้นและหลักสูตรของโรงเรียนได้</p></section>
<section id="lessons"><h2>📘 เนื้อหาบทเรียน</h2>{lesson_html}</section>
<section id="pretest" class="quizbox"><h2>📝 แบบทดสอบก่อนเรียน</h2><p>ตอบคำถามให้ครบ แล้วกด “ตรวจคำตอบ” เพื่อดูคะแนน</p><div id="pre-quiz"></div><button onclick="grade('pre')">ตรวจคำตอบ</button><button class="secondary" onclick="resetQuiz('pre')">เริ่มใหม่</button><div id="pre-result" aria-live="polite"></div></section>
<section id="posttest" class="quizbox"><h2>✅ แบบทดสอบหลังเรียน</h2><p>ทำแบบทดสอบหลังจากอ่านเนื้อหาทั้งหมดแล้ว</p><div id="post-quiz"></div><button onclick="grade('post')">ตรวจคำตอบ</button><button class="secondary" onclick="resetQuiz('post')">เริ่มใหม่</button><div id="post-result" aria-live="polite"></div></section>
<section><h2>📎 เพิ่มสื่อการสอนของครู</h2><p>เพิ่มลิงก์วิดีโอหรือเอกสารที่ต้องการให้นักเรียนศึกษาได้ โดยแก้ไขไฟล์ HTML นี้</p><p class="muted">ตัวอย่าง: <code>&lt;a href="URL-สื่อการสอน"&gt;เปิดสื่อการสอน&lt;/a&gt;</code> หากเป็นไฟล์ในโฟลเดอร์เดียวกัน ให้ใส่ชื่อไฟล์ เช่น ใบงาน.pdf</p></section>
</main><footer>เว็บไซต์บทเรียนออนไลน์ • HTML + CSS + JavaScript • สามารถเผยแพร่ผ่าน GitHub Pages</footer>
<script>
const questions = {qjson};
function renderQuiz(id){{
 const root=document.getElementById(id+'-quiz');
 root.innerHTML=questions.map((item,i)=>`<div class="question" style="margin:18px 0"><strong>${{i+1}}. ${{item.q}}</strong>${{item.opts.map((o,j)=>`<label class="option"><input type="radio" name="${{id}}-${{i}}" value="${{j}}">${{o[0]}}</label>`).join('')}}</div>`).join('');
}}
function grade(id){{
 let score=0,answered=0;
 questions.forEach((q,i)=>{{
  const chosen=document.querySelector(`input[name="${{id}}-${{i}}"]:checked`);
  if(chosen){{answered++;if(Number(chosen.value)===q.correct)score++;}}
 }});
 const percent=Math.round(score/questions.length*100);
 document.getElementById(id+'-result').innerHTML=`<div class="result"><strong>ผลคะแนน: ${{score}} / ${{questions.length}} คะแนน (${{percent}}%)</strong><br>ตอบแล้ว ${{answered}} จาก ${{questions.length}} ข้อ<br>${{percent>=80?'ทำได้ดีมาก ลองทบทวนเพิ่มเติมเพื่อให้แม่นยำยิ่งขึ้น':percent>=50?'ทำได้ดี ควรกลับไปอ่านหัวข้อที่ยังไม่มั่นใจ':'ลองอ่านบทเรียนอีกครั้ง แล้วทำแบบทดสอบใหม่'}}<div class="progress" style="margin-top:10px"><span style="width:${{percent}}%"></span></div></div>`;
}}
function resetQuiz(id){{renderQuiz(id);document.getElementById(id+'-result').innerHTML='';}}
renderQuiz('pre');renderQuiz('post');
</script></body></html>'''
    with open(os.path.join(folder, "index.html"), "w", encoding="utf-8") as f:
        f.write(html)

# Instructions
files["README.md"] = """# ห้องเรียนออนไลน์ (HTML สำหรับ GitHub Pages)

## โครงสร้างโฟลเดอร์
- `index.html` — หน้าหลักเลือกวิชา
- `วิทยาการคำนวณ/index.html` — บทเรียนและแบบทดสอบ
- `คอมพิวเตอร์/index.html` — บทเรียนและแบบทดสอบ
- `การงานอาชีพ/index.html` — บทเรียนและแบบทดสอบ

## วิธีเปิดใช้งาน
1. แตกไฟล์ ZIP
2. เปิด `index.html` ในเว็บเบราว์เซอร์เพื่อทดสอบ
3. สร้าง Repository ใหม่บน GitHub
4. อัปโหลดไฟล์และโฟลเดอร์ทั้งหมด โดยให้ `index.html` อยู่ที่ระดับบนสุด
5. ไปที่ **Settings → Pages**
6. เลือก **Deploy from a branch**, เลือก branch `main` และ folder `/ (root)` แล้วกด Save
7. รอสักครู่ จากนั้นเปิด URL ที่ GitHub Pages แสดงให้

## วิธีแก้ไขเนื้อหา
- เปิด `index.html` ของแต่ละวิชาด้วย VS Code หรือโปรแกรมแก้ไขข้อความ
- แก้ชื่อบทเรียน คำอธิบาย และสรุปเนื้อหาในส่วนบทเรียน
- คำถามและตัวเลือกอยู่ในตัวแปร `const questions = [...]` ในแท็ก `<script>`
- ตัวอย่างนี้ใช้แบบทดสอบปรนัย 4 ข้อเพื่อสาธิต สามารถเพิ่มคำถามได้โดยเพิ่มรายการในอาร์เรย์ `questions`
- คะแนนคำนวณในเบราว์เซอร์ ไม่เก็บชื่อ คะแนน หรือประวัติผู้เรียนลงฐานข้อมูล

## ข้อควรรู้
เป็นเว็บไซต์แบบ Static HTML/CSS/JavaScript ไม่ต้องติดตั้งเซิร์ฟเวอร์หรือฐานข้อมูล หากต้องการระบบเข้าสู่ระบบ บันทึกคะแนนถาวร หรือแดชบอร์ดครู ต้องเพิ่มบริการจัดเก็บข้อมูลหรือ backend ภายหลัง
"""
for path, content in files.items():
    with open(os.path.join(base, path), "w", encoding="utf-8") as f:
        f.write(content)

zip_path = "/mnt/data/บทเรียนออนไลน์_GitHub.zip"
with zipfile.ZipFile(zip_path, "w", zipfile.ZIP_DEFLATED) as z:
    for root, dirs, filenames in os.walk(base):
        for fn in filenames:
            full = os.path.join(root, fn)
            arc = os.path.relpath(full, base)
            z.write(full, arc)

print("สร้างชุดเว็บไซต์เรียบร้อย:", zip_path)
print("ภายในมีหน้าหลัก 1 ไฟล์, หน้าแต่ละวิชา 3 ไฟล์ และ README.md")
