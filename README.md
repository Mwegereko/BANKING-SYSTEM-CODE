class Bank(object):
    def __init__(self,bankId,name,location):
        self.bankId = bankId
        self.name = name
        self.location = location

    def detail(self):
        print("\n\t\t Name:",self.name,"\n\t\t Location:",self.location,"\n\t\t CEDAT BANK:",self.bankId,"\n\n\n")

    
class Teller(Bank):
    
    def __init__(self,Bank,Id,Name):
        self.Bank = Bank
        self.Id = Id
        self.Name = Name
        
    def detail(self):
        print("\nBANK: ",self.Bank.name,"TELLER ID",self.Id,"TELLER NAME:",self.Name)
        
    def CollectMoney(Customer,amt):
        if(Customer.Bank.bankId == self.Bank.bankId):
            Customer.AccountBal+=amt
            print("Collecting Money")
        else:
            print("Look For Your BANK")

    def OpenAccount():
        print("Opening Account")

    def CloseAcount():
        print("Closing Account")

    def loanRequest():
        print("Load Request")

    def ProvideInfo():
        print("Provide Info")

    def IssueCard():
        print("Issue Card")


## %%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%        
class Customer(Bank):
    AccountBal = 0
    LoanAmt = 0
    def __init__(self,Bank,Id,Name,Address,PhoneNo,AcctNo):
        self.Bank = Bank
        self.Name = Name
        self.Id = Id
        self.Address = Address
        self.PhoneNo = PhoneNo
        self.AcctNo = AcctNo

    def detail(self):
        print("="*57,
              "\n\t\t Customer's ID:",self.Id,
              "\n\t\t BANK:",self.Bank.name,
              "\n\t\t NAME:",self.Name,
              "\n\t\t ADDRESS:",self.Address,
              "\n\t\t PHONE NO:",self.PhoneNo,
              "\n\t\t AC\\NO:",self.AcctNo+"\n"+"="*57
              )

    def GeneralInquiry(self):
        print("General Inquiry")

    def DepositMoney(self, amt):
        self.AccountBal += amt
        print("deposit of ",amt," Shs\n")
    
    def WithdrawMoney(self, amt):
        if(amt < self.AccountBal):
            self.AccountBal -= amt
            print("withdraw Amount ",amt," Shs\n")
        else:
            print("PLEASE YOU HAVE INSUFFICIENT BALANCE")

    def OpenAccount(self):
        print("open account")

    def CloseAcount(self):
        print("Close account")

    def ApplyForLoan(self, amt):
        print("apply for loan")

    def RequestCard(self):
        print("request card")

class Account(Customer):
    def __init__(self, Customer,Id,CustomerId):
        self.Customer = Customer
        self.Id = Id
        self.CustomerId = CustomerId

class Loan(Customer):
    def __init__(self, Customer,Id,CustomerId):
        self.Customer = Customer
        self.Id = Id
        self.CustomerId = CustomerId

class Savings(Account):
    def __init__(self,Account,Id,CustomerId):
        self.Account = Account
        self.Id = Id
        self.CustomerId = CustomerId
        print("SAVINGS: ",self.Account.AccountBal)
              
class Checking(Account):
    def __init__(self,Account,Id,CustomerId):
        self.Account = Account
        self.Id = Id
        self.CustomerId = CustomerId
        print("checking... \n BALANCE: ",self.Account.AccountBal)
#BANK BRANCHES  
cb1 = Bank(1000054,"CEDAT BANK 1","NAKAWA")
cb2= Bank(1000052,"CEDAT BANK 2","WANDEGEYA")

cb1.detail()
cb2.detail()

#CEDAT BANK 1 TELLERS
cb1_T1 = Teller(cb1,2400622,"Ahereza John")
cb1_T2 = Teller(cb1,2303342,"Ainebyona Noah")
cb1_T3 = Teller(cb1,2100230,"Muwonge Alex")

cb1_T1.detail()
cb1_T2.detail()
cb1_T3.detail()

# CEDAT BANK 2 TELLERS
cb2_T1 = Teller(cb2,213456,"Muhanga Alice")
cb2_T2 = Teller(cb2,134453,"Kahondo Allan")
cb2_T3 = Teller(cb2,123444,"Kanungu Amos")
#
cb2_T1.detail()
cb2_T2.detail()
cb2_T3.detail()



### CUSTOMERS
print("CUSTOMERS of ",cb1.name,"\n","."*60)
CS_cb1 = [
    Customer(cb1,10051,"Yebazibwe Andrew","Nakawa","0784784774","0211547854591"),
    Customer(cb1,10052,"Mwegereko Peter","Lubaga","0772345455","0415432156708"),
    Customer(cb1,10053,"Kato Moses","Namugongo","0782345554","0411234567780"),
    Customer(cb1,10054,"Tayebwa Junior","Lubaga","0751233344","0311545452749"),
    Customer(cb1,10055,"Mugabi Shafic","Mukono","0780000007","0470545454513"),
    Customer(cb1,10056,"Namuwooya Jane","Seeta","0782345334","0411845494546"),
    Customer(cb1,10057,"Nakisseka Gladys","Kawempe","0754525136","0711546454105"),
    Customer(cb1,10058,"Namukonya Lucky","Gayaaza","0754645459","0611545474540"),
    Customer(cb1,10059,"Mugalu Joshua","Kireeka","0774535450","0413545658570"),
    Customer(cb1,10060,"Tamale Jimmmy","Gayaaza","0752535457","0771548804547")
    ]

for sc in CS_cb1:    
    print(sc.detail())

print("CUSTOMERS of ",cb2.name,"\n","."*60)
CS_cb2 = [
    Customer(cb2,58490,"Namusoke Esther","Luggogo","0772225607","5211540854597"),
    Customer(cb2,58491,"Kisekka Judy","Kireka","0778268784","6415438156707"),
    Customer(cb2,58492,"Boniface Okello","Kitintale","0756678136","0751239567781"),
    Customer(cb2,58493,"Opule Edward","Kireka","0757507966","3311547452748"),
    Customer(cb2,58494,"Mukooza Ben","Namugongo","0784507618","1470566454517"),
    Customer(cb2,58495,"Kasolo Jerry","Kamapala","0784530306","3411847494549"),
    Customer(cb2,58496,"Mulindwa Paul","Kawempe","0754991136","2711546457106"),
    Customer(cb2,58497,"Lukaku Martin","kawempe","0754545803","3611565474545"),
    Customer(cb2,58498,"ALupo Jeska","gayaaza","0772581750","0493545058570"),
    Customer(cb2,58499,"Sande Paul","Bunamwaya","0752001457","5771548803842")
    ]

for sc in CS_cb2:    
    print(sc.detail())

#### withdraw and deposit
# ACCOUNT
CB1 = Customer(cb1,55848,"Kisya Moses","Kalangala","+256780589893","98556601111254")
CB1_A = Account(CB1,25004,1)
class CLIMenu(object):

    def __init__(self, options: list):
        self.options=options

    def PrintCLIMenu(self):
        print('=' * 30, '\t WELCOME TO CEDAT BANK\n\tWe Are Here To Serve You\n\t\tTELLER1', '=' * 30, sep='\n')
        print("Branch:WANDEGEYA\nBankID:10002746889")
        print("PLEASE CHOOSE THE DESIRED OPTION BELOW :\n ", *self.options,
              sep='\n')
        print()
    def GetUserInput(self):
        return input(">>>: ")
def RegisterCustomer():
    RegisterCustomerForm = [input("NATIONAL ID NUMBER : "), input("YOUR FULL NAME: "),
                                input("DATE OF BIRTH (DD/MM/YYYY) : "),
                                input("HOME TOWN: "), input("PHONE NUMBER : "), input("VALID EMAIL ADDRESS : ")]
    cursor.execute("INSERT into customer VALUES(?,?,?,?,?,?)", *RegisterCustomerForm)
    cnxn.commit()
    print("REGISTRATION SUCCESSFUL")
    cursor.execute("INSERT into account VALUES(?,?,0)", RegisterCustomerForm[0], RegisterCustomerForm[1])
    cnxn.commit()
    
    def  ViewCustomer():
        CustToView=input("PLEASE ENTER THE NATIONAL IDENTITY CARD NUMBER OF THE CUSTOMER YOU WISH TO VIEW : ")
        cursor.execute("SELECT * FROM customer WHERE Cust_NIC=?",CustToView)
        columns = [column[0] for column in cursor.description]
        print('\t'.join(str(i) for i in columns),end="")
        print('\n')
        for row in cursor.fetchall():
            print ('\t'.join(str(j)for j in row))
        input("\n==========PRESS ENTER KEY TO RETURN TO THE PREVIOUS MENU==========")

    def ViewAllCustomers():
        cursor.execute("SELECT * FROM customer") 
    columns = [column[0] for column in cursor.description]
    print('\t'.join(str(i) for i in columns), end="")
    print('\n')
    for row in cursor.fetchall():
        print('\t'.join(str(j) for j in row))
    input("\n==========PRESS ENTER KEY TO RETURN TO THE PREVIOUS MENU==========")
    
class Transaction:

    def __init__(self,acct,amt):
        self.acct=acct
        self.amt=amt

    def Deposit(self):
        cursor.execute("UPDATE account SET Acct_Bal=Acct_Bal+? WHERE Acct_NO=?",self.amt,self.acct)
        cnxn.commit()
        print("YOU'VE DEPOSITED %s TO ACCOUNT NUMBER %s" % (self.amt,self.acct))
    def Withdrawal(self):
        cursor.execute("UPDATE account SET Acct_Bal=Acct_Bal-? WHERE Acct_NO=?",self.amt,self.acct)
        cnxn.commit()
        print("YOU'VE  WITHDRAWN  %s FROM ACCOUNT NUMBER %s" % (self.amt, self.acct))


if __name__=='__main__':
     while True:
        MainMenu=CLIMenu(['\t1.ACCESS CUSTOMER DETAILS','\t2.ACCESS TRANSACTION PORTAL','\t3.EXIT'])
        MainMenu.PrintCLIMenu()
        UserInput=MainMenu.GetUserInput()
        if UserInput =='1':
            while True:
                CustomerMenu = CLIMenu(['\t1.REGISTER CUSTOMER', '\t2.VIEW CUSTOMER',
                                              '\t3.VIEW ALL CUSTOMERS','\t4.GO TO PREVIOUS MENU'])
                CustomerMenu.PrintCLIMenu()
                UserInput=CustomerMenu.GetUserInput()
                if UserInput == '1':
                    RegisterCustomer()
                    continue
                if UserInput == '2':
                    ViewCustomer()
                    continue
                if UserInput == '3':
                    ViewAllCustomers()
                    continue
                if UserInput == '4':
                    break
        elif UserInput == '2':
            AcctToTransact=input("PLEASE ENTER THE ACCOUNT NUMBER : ")
            AmtToTransact=input("PLEASE ENTER THE TRANSACTION AMOUNT : ")
            trnsct=Transaction(AcctToTransact,AmtToTransact)
            TransactionMenu = CLIMenu(['\t1.DEPOSIT MONEY',
                                             '\t2.WITHDRAW MONEY', '\t3.GO TO PREVIOUS MENU'])
            TransactionMenu.PrintCLIMenu()
            UserInput = TransactionMenu.GetUserInput()
            if UserInput == '1':
                trnsct.Deposit()
                continue
            if UserInput == '2':
                trnsct.Withdrawal()
                continue
            if UserInput == '3':
                continue
        elif UserInput == '3':
            break

cnxn.close()
quit()


