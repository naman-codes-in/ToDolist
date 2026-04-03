# ToDolist
A To Do list which contains the work and it's priority and status 
class ToDoList:
    def __init__(self):
        self.tasks = []

    def add_task(self):
        name = input("Enter the name of task: ")
        Priority = input("Enter your Priority: ")
        self.tasks.append((name , Priority))
        with open("ToDoList.txt","a") as f:
            f.write(f"{name} {Priority}\n")

    def task_analys(self):
        with open("ToDoList.txt","r") as f:
            lines = f.readlines() 
    
        for line in lines:
            parts = line.split()
            name = parts[0]
            priority = parts[1]
            print(f"Task: {name} | Priority: {priority}")
            Status = input("Completed hai? (yes/no): ")
            if Status == "yes":
                with open("ToDoList.txt","a") as f:
                    f.write(f"{name} DONE\n")
                print(f"{name} -- DONE! ✅")
t = ToDoList()

while True:
    print("1, Task add karo")
    print("2, Task dekho")
    print("3, Exit")
    choice = input("Kya karna hai? ")

    if choice == "1":
        t.add_task()
    elif choice == "2":
        t.task_analys()
    elif choice == "3":
        break
