# pythontanaporn
#import sqlite3
#conn = sqlite3.connect (r'D:\python naruephat\example.db')
#c = conn.cursor()
#c.execute ('''CREATE TABLE mailst(ลำดับที่ integer PRIMARY KEY AUTOINCREMENT,
#ชื่อ_นามสกุล varchar(30)NOT NULL,
#email varchar(100)NOT NULL,
##เพศ   varchar(30)NOT NULL,
#อายุ   varchar(30)NOT NULL,
#ชั้นปี   varchar(30)NOT NULL)''')
#conn.commit()
#conn.close()
import sqlite3
def menu():
    global mail
    print('---Registration---\n','='*20)
    print('add student [a]\nshow student [s]\nedit student][e]\ndelete[d]\nexit[x]')
    mail =str(input(' '))
def show():
    conn = sqlite3.connect(r'D:\python naruephat\example.db')
    c = conn.cursor()
    c.execute ('''SELECT * FROM mailst''')
    result = c.fetchall()
    print('number:name          :e-mail      :sex  :   age :  year :')
    for x in result :
        print(x)
def addst():
    num = int(input('input number'))
    name = str(input('input name=>'))
    email = str(input('input e-mail=>'))
    sex = str(input('input sex=>'))
    age = int(input('input age=>'))
    year = int(input('input year=>'))
    import sqlite3
    conn = sqlite3.connect(r'D:\python naruephat\example.db')
    c = conn.cursor()
    try:
        data = (name,e-m,sex,age,year,num)
        c.execute('''UPDATE mailst SET ชื่อ_นามสกุล  =?,email =?,เพศ =?,อายุ  =?,ชั้นปี =? WHERE ลำดับที่ =?''',data)
        conn.commit()
        c.close()
    except sqlite3.Error as e:
        print (e)
    finally :
        if conn :
            conn.close()
def ad():
    conn = sqlite3.connect(r'D:\python naruephat\example.db')
    c = conn.cursor()
    try:
        name2 = str(input('input name=>'))
        email2 = str(input('input e-mail=>'))
        sex2 = str(input('input sex=>'))
        age2 = int(input('input age=>'))
        year2 = int(input('input year=>'))
        data =(name2,email2,sex2,age2,year2)
        c.execute('INSERT INTO mailst  ( ชื่อ_นามสกุล ,email,เพศ,อายุ,ชั้นปี)VALUES (?,?,?,?,?)',data)
        conn.commit()
        c.close ()
    except sqlite3.Error as e:
        print (e)
    finally :
        if conn :
            conn.close()
def fdel():
    conn = sqlite3.connect(r'D:\python naruephat\example.db')
    c = conn.cursor()
    try:
        data3 = str(input('Please enter ชื่อ_นามสกุล : '))
        mydata = c.execute('DELETE FROM mailst WHERE ชื่อ_นามสกุล =?', (data3,))
        #DELETE FROM your_mailst;    
        #DELETE FROM sqlite_sequence WHERE name = 'your_mailst';
        conn.commit()
        c.close()
    except sqlite3.Error as e:
        print (e)
    finally :
        if conn :
            conn.close()
while True:
    menu()
    if  mail == 'a' :
        ad()
    if  mail == 's' :
        show()
    if  mail == 'e' :
        addst()
    if  mail == 'd' :
        fdel()
    if  mail == 'x' :
        print('exit program  yes/no')
        ex=str(input(' '))
        if ex == 'yes':
            break
