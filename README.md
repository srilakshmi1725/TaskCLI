import os

TASKS_FILE = "tasks.txt"

def load_tasks():
    if not os.path.exists(TASKS_FILE):
        return []
    with open(TASKS_FILE, "r") as file:
        return [line.strip() for line in file.readlines()]

def save_tasks(tasks):
    with open(TASKS_FILE, "w") as file:
        for task in tasks:
            file.write(task + "\n")

def show_menu():
    print("\nTaskCLI - Simple To-Do App")
    print("1. View tasks")
    print("2. Add task")
    print("3. Complete task")
    print("4. Exit")

def main():
    tasks = load_tasks()
    while True:
show_menu()
        choice = input("Enter choice (1-4): ")
        if choice == "1":
            print("\nYour Tasks:")
            for idx, task in enumerate(tasks, 1):
                print(f"{idx}. {task}")
        elif choice == "2":
            task = input("Enter task: ")
            tasks.append(task)
            save_tasks(tasks)
        elif choice == "3":
            index = int(input("Enter task number to mark complete: ")) - 1
            if 0 <= index < len(tasks):
                tasks.pop(index)
                save_tasks(tasks)
                print("✅ Task completed!")
            else:
                print("❌ Invalid task number.")
        elif choice == "4":
            print("👋 Exiting. Bye!")
            break
        else:
            print("❌ Invalid choice.")

if _name_ == "_main_":
    main()# TaskCLI
