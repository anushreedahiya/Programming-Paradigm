// RESTAURANT ORDERING SYSTEM
#include <iostream>
#include <iomanip>
#include <string>

using namespace std;

class MenuItem {
public:
    MenuItem(string name, double price) : name(name), price(price), quantity(0) {}

    virtual double calculatePrice() const {
        return price;
    }

    virtual void display() const {
        cout << setw(25) << left << name << setw(10) << right << "Rs. " << calculatePrice() << endl;
    }

    string getName() const {
        return name;
    }

    int getQuantity() const {
        return quantity;
    }

    void setQuantity(int newQuantity) {
        quantity = newQuantity;
    }

private:
    string name;
    double price;
    int quantity;
};

class Beverage : public MenuItem {
public:
    Beverage(string name, double price) : MenuItem(name, price) {}
};

class Appetizer : public MenuItem {
public:
    Appetizer(string name, double price) : MenuItem(name, price) {}
};

class Dessert : public MenuItem {
public:
    Dessert(string name, double price) : MenuItem(name, price) {}
};

void selectItems(MenuItem* menu[], int menuSize, MenuItem*** order, int& orderSize) {
    int choice;
    int quantity;

    do {
        cout << "Enter the number of the item (enter 0 to stop ordering): ";
        cin >> choice;

        if (choice >= 1 && choice <= menuSize) {
            cout << "Enter the quantity: ";
            cin >> quantity;

            MenuItem* newItem = new MenuItem(*menu[choice - 1]);
            newItem->setQuantity(quantity);

            MenuItem** newOrder = new MenuItem*[orderSize + 1];
            for (int i = 0; i < orderSize; ++i) {
                newOrder[i] = (*order)[i];
            }

            newOrder[orderSize] = newItem;

            delete[] (*order);

            (*order) = newOrder;
            orderSize++;
        } else if (choice != 0) {
            cout << "Invalid choice. Please select a valid item.\n";
        }

    } while (choice != 0);
}

void deleteItem(MenuItem*** order, int& orderSize) {
    if (orderSize == 0) {
        cout << "Order is empty. Cannot delete item.\n";
        return;
    }

    cout << "Enter the item number to delete: ";
    int itemNumber;
    cin >> itemNumber;

    if (itemNumber >= 1 && itemNumber <= orderSize) {
        delete (*order)[itemNumber - 1];

        MenuItem** newOrder = new MenuItem*[orderSize - 1];
        int newIndex = 0;
        for (int i = 0; i < orderSize; ++i) {
            if (i != itemNumber - 1) {
                newOrder[newIndex++] = (*order)[i];
            }
        }

        delete[] (*order);

        (*order) = newOrder;
        orderSize--;
        cout << "Item deleted successfully.\n";
    } else {
        cout << "Invalid item number.\n";
    }
}

void displayBill(MenuItem** order, int orderSize) {
    if (orderSize == 0) {
        cout << "No items in the order.\n";
        return;
    }

    cout << "Your Order:\n";
    double total = 0.0;

    cout << setfill('-') << setw(40) << "-" << setfill(' ') << endl;
    cout << setw(5) << left << "Qty" << setw(25) << left << "Item" << setw(10) << right << "Price\n";
    cout << setfill('-') << setw(40) << "-" << setfill(' ') << endl;

    for (int i = 0; i < orderSize; i++) {
        cout << setw(5) << left << order[i]->getQuantity();
        order[i]->display();
        total += order[i]->calculatePrice();
    }

    cout << setfill('-') << setw(40) << "-" << setfill(' ') << endl;
    cout << setw(30) << left << "Total:" << setw(10) << right << "Rs. " << total << endl;
}

void displayMenu(MenuItem* menu[], int menuSize) {
    cout << "\n Welcome to ESSPRESSO EXPRESS ! \n";
    cout << "\nMenu:\n";
    cout << setw(5) << left << "No." << setw(25) << left << "Item" << setw(25) << right << "Price\n";
    cout << setfill('-') << setw(55) << "-" << setfill(' ') << endl;

    for (int i = 0; i < menuSize; i++) {
        cout << setw(5) << left << (i + 1) << setw(25) << left << menu[i]->getName() << setw(25) << right
             << "Rs. " << menu[i]->calculatePrice() << endl;
    }

    cout << setfill('-') << setw(55) << "-" << setfill(' ') << endl;
}

int main() {
    const int menuSize = 15;
    MenuItem* menu[menuSize];

    menu[0] = new Beverage("Americano", 50.0);
    menu[1] = new Beverage("Latte", 80.0);
    menu[2] = new Beverage("Cappuccino", 85.0);
    menu[3] = new Beverage("Mocha latte", 90.0);
    menu[4] = new Beverage("Frappuccino", 110.0);
    menu[5] = new Dessert("Tiramisu", 300.0);
    menu[6] = new Dessert("Cheese cake", 360.0);
    menu[7] = new Dessert("Chocolave cake", 100.0);
    menu[8] = new Dessert("Strawberry Shortcake", 200.0);
    menu[9] = new Dessert("Macaron", 250.0);
    menu[10] = new Appetizer("Garlic Bread", 180.0);
    menu[11] = new Appetizer("Potato Wedges", 100.0);
    menu[12] = new Appetizer("Onion Rings", 170.0);
    menu[13] = new Appetizer("Ratatouille", 500.0);
    menu[14] = new Appetizer("Chicken nuggets", 400.0);

    displayMenu(menu, menuSize);

    MenuItem** order = NULL;
    int orderSize = 0;

    int option;
    do {
        cout << "\nMenu Options:\n";
        cout << "1. Add items to the order\n";
        cout << "2. Delete an item from the order\n";
        cout << "3. Display Bill\n";
        cout << "0. Exit\n";
        cout << setfill('-') << setw(40) << "-" << setfill(' ') << endl;
        cout << "Enter your choice: ";
        cin >> option;

        switch (option) {
            case 1:
                selectItems(menu, menuSize, &order, orderSize);
                break;
            case 2:
                deleteItem(&order, orderSize);
                break;
            case 3:
                displayBill(order, orderSize);
                break;
            case 0:
                cout << "Exiting...\n";
                break;
            default:
                cout << "Invalid choice. Please enter a valid option.\n";
        }

    } while (option != 0);

    for (int i = 0; i < menuSize; i++) {
        delete menu[i];
    }

    for (int i = 0; i < orderSize; i++) {
        delete order[i];
    }

    delete[] order;

    return 0;
}
