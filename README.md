# task-tracker
Simple Python CLI task tracker app
tasks = []

def show_menu():
    print("\n--- Task Tracker ---")
    print("1. Add Task")
    print("2. View Tasks")
    print("3. Mark Task Complete")
    print("4. Exit")

def add_task():
    task = input("Enter a new task: ")
    tasks.append({"task": task, "done": False})
    print(f"Task '{task}' added.")

def view_tasks():
    if not tasks:
        print("No tasks yet.")
        return
    for i, t in enumerate(tasks):
        status = "✓" if t["done"] else "✗"
        print(f"{i+1}. [{status}] {t['task']}")

def complete_task():
    view_tasks()
    try:
        num = int(input("Enter the task number to mark as complete: "))
        tasks[num-1]["done"] = True
        print("Task marked as complete.")
    except (IndexError, ValueError):
        print("Invalid number.")

while True:
    show_menu()
    choice = input("Choose an option: ")
    if choice == '1':
        add_task()
    elif choice == '2':
        view_tasks()
    elif choice == '3':
        complete_task()
    elif choice == '4':
        print("Goodbye!")
        break
    else:
        print("Invalid option.")