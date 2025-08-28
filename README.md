#include <iostream>
#include <string>
using namespace std;

const int MAX_ORDERS = 50;
const double PRICE_PER_MAGWINYA = 5.25;

int orderIDs[MAX_ORDERS];
string customers[MAX_ORDERS];
int quantities[MAX_ORDERS];
double totals[MAX_ORDERS];
int orderCount = 0;

// Function to add a new order
void addOrder() {
    if (orderCount >= MAX_ORDERS) {
        cout << "Order list is full!\n";
        return;
    }

    cout << "Enter Order ID: ";
    cin >> orderIDs[orderCount];
    cout << "Enter Customer Name: ";
    cin >> customers[orderCount];
    cout << "Enter Number of Magwinyas: ";
    cin >> quantities[orderCount];

    totals[orderCount] = quantities[orderCount] * PRICE_PER_MAGWINYA;
    cout << "Order added successfully!\n";
    orderCount++;
}

// Function to display all orders
void displayOrders() {
    if (orderCount == 0) {
        cout << "No orders found.\n";
        return;
    }

    for (int i = 0; i < orderCount; i++) {
        cout << "Order ID: " << orderIDs[i]
             << ", Customer: " << customers[i]
             << ", Number of Magwinyas: " << quantities[i]
             << ", Total: " << totals[i] << endl;
    }
}

// Function to find order by ID
void findOrder() {
    int searchID;
    cout << "Enter Order ID to find: ";
    cin >> searchID;

    bool found = false;
    for (int i = 0; i < orderCount; i++) {
        if (orderIDs[i] == searchID) {
            cout << "Order ID: " << orderIDs[i]
                 << ", Customer: " << customers[i]
                 << ", Number of Magwinyas: " << quantities[i]
                 << ", Total: " << totals[i] << endl;
            found = true;
            break;
        }
    }
    if (!found) cout << "Order with Order ID " << searchID << " not found.\n";
}

// Function to calculate total revenue
void calculateRevenue() {
    double totalRevenue = 0;
    for (int i = 0; i < orderCount; i++) {
        totalRevenue += totals[i];
    }
    cout << "Total Revenue: " << totalRevenue << endl;
}

int main() {
    int choice;
    do {
        cout << "\nOrder Management System\n";
        cout << "1. Add a new order\n";
        cout << "2. Display all orders\n";
        cout << "3. Find an order by Order ID\n";
        cout << "4. Calculate total revenue\n";
        cout << "5. Exit\n";
        cout << "Enter your choice (1-5): ";
        cin >> choice;

        switch (choice) {
            case 1: addOrder(); break;
            case 2: displayOrders(); break;
            case 3: findOrder(); break;
            case 4: calculateRevenue(); break;
            case 5: cout << "Exiting program...\n"; break;
            default: cout << "Invalid choice. Try again.\n";
        }
    } while (choice != 5);

    return 0;
}
