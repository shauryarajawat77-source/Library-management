# Library-management
lib = {}
f = open("lib.txt","a+")
def add():
    global f
    y = input("Enter Book Name: ")
    y = y.capitalize()
    x =  input("Enter Avilability, [Avilable] OR [Borrowed]: ")
    x = x.capitalize()
    lib[y] = x
    f.writelines(f"{y},{x}\n")
def show():
    global f
    f.seek(0)
    print(f.read())
def search():
    global f
    f.seek(0)
    u = input("Enter Book Name: ")
    u = u.capitalize()
    v = input("Enter Avilablity")
    v = v.capitalize()
    k = (f"{u},{v}\n")
    d = list(f)
    if k in d:
        print("Book Found")
        print(f"{u}\t{v}")
    else:
        print("Book Not Found")
def delete():
    global f
    f.seek(0)
    u = input("Enter Book Name: ")
    u = u.capitalize()
    v = input("Enter Avilablity: ")
    u = u.capitalize()
    lis = list(f)
    k = (f"{u},{v}\n")
    if k in lis:
        lis.remove(k)
        f.seek(0)
        f.truncate()
        f.writelines(lis)
    else:
        print("Book Not Found")
def edit():
    global f
    f.seek(0)
    lib.clear()
    u = input("Enter Book Name: ")
    u = u.capitalize()
    v = input("Enter New Avilablity: ")
    v = v.capitalize()
    for lines in f:
        k,c = lines.strip().split(',')
        lib[k] = c
    if u in lib:
        lib[u] = v
    f.seek(0)
    f.truncate()
    for books,avilablity in lib.items():
        f.writelines(f"{books},{avilablity}\n")
def ret():
    global f
    f.seek(0)
    lib.clear()
    u = input("Enter Book Name: ")
    u = u.capitalize()
    for lines in f:
        c,x = lines.strip().split(',')
        lib[c] = x
    if u in lib:
            l = "Available"
            lib[u] = l
    if u not in lib:
            print("Book Not Found")
    f.seek(0)
    f.truncate()
    for books,avilablity in lib.items():
        f.writelines(f"{books},{avilablity}\n")
    print("Book Returned Successfully")  
def borrow():
    global f 
    f.seek(0)
    lib.clear()
    u = input("Enter Book Name: ")
    u = u.capitalize()
    for line in f:
        c,d = line.strip().split(",")
        lib[c]=d
    if u in lib:
            l = "Borrowes"
            lib[u] = l
    if u not in lib:
            print("Book Not Found")
    f.seek(0)
    f.truncate()
    for l,m in lib.items():
        f.writelines(f"{l},{m}\n")
    print("Book Borrowed Successfully")
def avi():
    global f
    f.seek(0)
    lib.clear()
    u = input("Enter Book Name: ")
    u = u.capitalize()
    for lines in f:
        c,v = lines.strip().split(',')
        lib[c] = v
    if u in lib:
        x = lib.get(u)
        print(x)
    if u not in lib:
        print("Book Not Found")
def readbook():
    global f
    f.seek(0)
    print("Total Books")
    print(len(f.readlines()))
while True:
    print(30*'=')
    print("LIBRARA MANAGER".center(30))
    print(30*'=')
    print("[1] Add Book\n[2] Show Books\n[3] Search Books\n[4] Delete Book\n[5] Edit\n[6] Return Book\n[7] Borrow Book\n[8] Avilability Of Book\n[9] Total Books\n[10] Exit".center(30))
    print(30*'_')
    x = input("Enter Your Choice: ")
    print("\n")
    if x == '1':
        add()
    elif x == '2':
        show()
    elif x == '3':
        search()
    elif x == '4':
        delete()
    elif x == '5':
        edit()
    elif x == '6':
        ret()
    elif x == '7':
        borrow()
    elif x == '8':
        avi()
    elif x == '9':
        readbook()
    elif x == '10':
        print('Goodbye')
        print('x'*30)
        f.close()
        break
    else:
        print("invalid input")
