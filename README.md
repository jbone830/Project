class Setup:

    salesTax = 0
    sMenu = {}
    chicken = 0
    chips = 0
    drinks = 0
    burgers = 0
    jedi = 0
    total = 0
    

    def __init__(self):
        readFile = open('salestax.txt', 'r')
        line = readFile.readline()
        Setup.salesTax = float(line)
        readFile.close()

        readFile = open('menu.txt', 'r')
        for line in readFile:
            cBreak = line.split(',')
            Setup.sMenu[cBreak[0]] = float(cBreak[1])
           
            
            
            
        readFile.close()
        

    def getTax(self):

        return Setup.salesTax

    def setChicken(self):
        self.chicken += 1  # Adds to chicken sales only
        Setup.chicken += 1  # Adds to over all sales

    def setChips(self):
        self.chips += 1  # Adds to chips sales only
        Setup.chips += 1  # Adds to over all sales

    def setDrinks(self):
        self.burgers += 1  # Adds to drinks sales only
        Setup.burgers += 1  # Adds to over all sales

    def setBurgers(self):
        self.drinks += 1  # Adds to drinks sales only
        Setup.drinks += 1  # Adds to over all sales

    def setJedi(self):
        self.jedi += 1  # Adds to drinks sales only
        Setup.jedi += 1  # Adds to over all sales
       
        
    def getItems(self):
        return Setup.sMenu

    def getOrderCount(self):
        return Setup.orderCount

    def objOrderCount(self):
        return self.orderCount

    def getChicken(self):
        return Setup.chicken,  

    def objChicken(self):
        return self.chicken

    def getChips(self):
        return Setup.chips

    def objChips(self):
        return self.chips

    def getDrinks(self):
        return Setup.drinks

    def objDrinks(self):
        return self.drinks

    def getBurgers(self):
        return Setup.burgers

    def objBurgers(self):
        return self.burgers

    def getJedi(self):
        return Setup.jedi

    def objJedi(self):
        return self.jedi

    def resetChicken(self):
        Setup.chicken = Setup.chicken - self.chicken
        self.chicken = 0

    def resetBurgers(self):
        Setup.chicken = Setup.burgers - self.burgers
        self.burgers = 0

    def resetChips(self):
        Setup.chicken = Setup.chips - self.chips
        self.chips = 0

    def resetDrinks(self):
        Setup.chicken = Setup.drinks - self.drinks
        self.drinks = 0

    def resetJedi(self):
        Setup.jedi = Setup.jedi - self.jedi
        self.jedi = 0

        
def menu(items):

   
    for i in items:
        print(i + "\t" + str(items[i]))
    print('T - Total')
    print("X - Cancel")
    print('E - Close sales')
    print('\n')

    select = input('Select Your Option : ')
    print('\n')
    return select
        
def main():

    count = 0

    mySet = Setup()
    
    food = mySet.setChicken()

    
                
    sTax = mySet.getTax()

    items = mySet.getItems()
   
    option = menu(items)
    
    while option.lower() != 'e':
        if (option.lower() == 'c'):
            mySet.setChicken()
            count += 1
        elif (option.lower() == 'h'):
            mySet.setChips
            count += 1
        elif (option.lower() == 'd'):
            mySet.setDrinks
            count += 1
        elif(option.lower() == 'b'):
            mySet.setBurgers
            count += 1
        elif(option.lower() == 'j'):
            mySet.setJedi
            count += 1
        elif (option.lower() == 'x'):
            print('CANCELING')
            print('\n')
            mySet.resetChicken()
            mySet.resetChips()
            mySet.resetDrinks()
            mySet.resetBurgers()
            mySet.resetJedi()
            count = 0
        elif (option.lower() == 't'):
            total = beforeTax(food)
            print('Totaling your order.....')
            print('The total number of items in your order is ', count)
            print('Your total before tax is: ', float(total))
            
        else:
            print('WRONG ENTRY')
                
       
            

        option = menu(items)

    print('The total number of chicken sold today is ', mySet.getChicken())
    cPrice = mySet.getChicken() * items['C - Chicken']
    print('The cost is ', cPrice)

def beforeTax(food):

    total = (Setup.chicken * 3) + (Setup.burgers * 10) + (Setup.chips * 5) + (Setup.drinks * 2) + (Setup.jedi * 99)

    return total

    
            
main()
