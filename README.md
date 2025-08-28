#include <iostream>
#include <string>
using namespace std;

// Constants
const int MAX_ORDERS = 50;
const double PRICE = 5.25;

// Arrays to store data
string orderID[MAX_ORDERS];
string customerName[MAX_ORDERS];
int magwinyaCount[MAX_ORDERS];
double totalCost[MAX_ORDERS];

// Track number of orders
int orderCount = 10;

// Load first 10 sample orders
void loadSamples() {
    orderID[0] = "101"; customerName[0] = "Thabo";    magwinyaCount[0] = 3; totalCost[0] = 15.75;
    orderID[1] = "102"; customerName[1] = "Lerato";   magwinyaCount[1] = 5; totalCost[1] = 30.50;
    orderID[2] = "103"; customerName[2] = "Nomvula";  magwinyaCount[2] = 2; totalCost[2] = 10.00;
    orderID[3] = "104"; customerName[3] = "Sipho";    magwinyaCount[3] = 4; totalCost[3] = 22.00;
    orderID[4] = "105"; customerName[4] = "Bongani";  magwinyaCount[4] = 6; totalCost[4] = 40.25;
    orderID[5] = "106"; customerName[5] = "Lindiwe";  magwinyaCount[5] = 1; totalCost[5] = 5.50;
    orderID[6] = "107"; customerName[6] = "Jabulani"; magwinyaCount[6] = 3; totalCost[6] = 18.00;
    orderID[7] = "108"; customerName[7] = "Ayanda";   magwinyaCount[7] = 2; totalCost[7] = 12.75;
    orderID[8] = "109"; customerName[8] = "Kgosi";    magwinyaCount[8] = 6; totalCost[8] = 28.00;
    orderID[9] = "110"; customerName[9] = "Refilwe";  magwinyaCount[9] = 4; totalCost[9] = 24.50;
}

// Add new order
void addOrder() {
    if (orderCount >= MAX_ORDERS) {
        cout << "No more space for new orders!\n";
        return;
    }
    // Generate new order ID
    int newID = stoi(orderID[orderCount - 1]) + 1;
    orderID[orderCount] = to_string(newID);

    cout << "Enter customer name: ";
    cin >> customerName[orderCount];
    cout << "Enter number of magwinyas: ";
    cin >> magwinyaCount[orderCount];

    totalCost[orderCount] = magwinyaCount[orderCount] * PRICE;

    cout << "Order saved! ID: " << orderID[orderCount] << endl;
    orderCount++;
}

// Show all orders
void showOrders() {
    if (orderCount == 0) {
        cout << "No orders to display.\n";
        return;
    }
    cout << "\n--- All Orders ---\n";
    for (int i = 0; i < orderCount; i++) {
        cout << "ID: " << orderID[i]
             << ", Name: " << customerName[i]
             << ", Qty: " << magwinyaCount[i]
             << ", Total: R" << totalCost[i] << endl;
    }
}

// Find specific order
void searchOrder() {
    string searchID;
    cout << "Enter Order ID: ";
    cin >> searchID;

    bool found = false;
    for (int i = 0; i < orderCount; i++) {
        if (orderID[i] == searchID) {
            cout << "ID: " << orderID[i]
                 << ", Name: " << customerName[i]
                 << ", Qty: " << magwinyaCount[i]
                 << ", Total: R" << totalCost[i] << endl;
            found = true;
            break;
        }
    }
    if (!found) cout << "Order not found.\n";
}

// Calculate revenue
void totalRevenue() {
    double revenue = 0;
    for (int i = 0; i < orderCount; i++) {
        revenue += totalCost[i];
    }
    cout << "Total Revenue = R" << revenue << endl;
}

// Main program
int main() {
    loadSamples();  // load first 10 orders

    int choice;
    do {
        cout << "\nMagwinya Magic Orders\n";
        cout << "1. Add Order\n";
        cout << "2. Show All Orders\n";
        cout << "3. Search Order\n";
        cout << "4. Total Revenue\n";
        cout << "5. Exit\n";
        cout << "Choose option: ";
        cin >> choice;

        if (choice == 1) addOrder();
        else if (choice == 2) showOrders();
        else if (choice == 3) searchOrder();
        else if (choice == 4) totalRevenue();
        else if (choice == 5) cout << "Goodbye!\n";
        else cout << "Invalid option, try again.\n";

    } while (choice != 5);

    return 0;
}
