# Task-3---ATM-Interface
import java.util.Scanner;

class BankAccount {
    private double balance;
    public BankAccount(double initialBalance) {
            balance = initialBalance;
                }
    public double getBalance() {
            return balance;
                }
    public void deposit(double amount) {
            balance += amount;
                }
    public boolean withdraw(double amount) {
            if (amount <= balance) {
                        balance -= amount;
                                    return true;
                                            }
                                                    return false;
                                                        }
                                                        }
class ATM {
    private BankAccount userAccount;
    public ATM(BankAccount account) {
            userAccount = account;
                }
    public void displayMenu() {
            System.out.println("Welcome to the ATM!");
                    System.out.println("1. Check Balance");
                            System.out.println("2. Withdraw");
                                    System.out.println("3. Deposit");
                                            System.out.println("4. Exit");
                                                }
    public void checkBalance() {
            System.out.println("Your balance is: $" + userAccount.getBalance());
                }
    public void withdraw(double amount) {
            boolean success = userAccount.withdraw(amount);
                    if (success) {
                                System.out.println("Withdrawn: $" + amount);
                                        } else {
                                                    System.out.println("Insufficient funds!");
                                                            }
                                                                }
    public void deposit(double amount) {
            userAccount.deposit(amount);
                    System.out.println("Deposited: $" + amount);
                        }
    public static void main(String[] args) {
            Scanner scanner = new Scanner(System.in);
        System.out.print("Enter your initial account balance: $");
                double initialBalance = scanner.nextDouble();
                        BankAccount userAccount = new BankAccount(initialBalance);
        ATM atm = new ATM(userAccount);
        boolean loggedIn = true;
        while (loggedIn) {
                    atm.displayMenu();
                                System.out.print("Select an option (1-4): ");
                                            int choice = scanner.nextInt();
            switch (choice) {
                            case 1:
                                                atm.checkBalance();
                                                                    break;
                                                                                    case 2:
                                                                                                        System.out.print("Enter withdrawal amount: $");
                                                                                                                            double withdrawAmount = scanner.nextDouble();
                                                                                                                                                atm.withdraw(withdrawAmount);
                                                                                                                                                                    break;
                                                                                                                                                                                    case 3:
                                                                                                                                                                                                        System.out.print("Enter deposit amount: $");
                                                                                                                                                                                                                            double depositAmount = scanner.nextDouble();
                                                                                                                                                                                                                                                atm.deposit(depositAmount);
                                                                                                                                                                                                                                                                    break;
                                                                                                                                                                                                                                                                                    case 4:
                                                                                                                                                                                                                                                                                                        loggedIn = false;
                                                                                                                                                                                                                                                                                                                            break;
                                                                                                                                                                                                                                                                                                                                            default:
                                                                                                                                                                                                                                                                                                                                                                System.out.println("Invalid option. Please choose again.");
                                                                                                                                                                                                                                                                                                                                                                            }
                                                                                                                                                                                                                                                                                                                                                                                    }
        System.out.println("Thank you for using the ATM!");
            }
            }
