```python
service_notes = []
```


```python
class Car:
    def __init__(self, name, manufacturer, model, option, year, colour, service_notes):
        self.name = name
        self.manufacturer = manufacturer
        self.model = model
        self.option = option
        self.year = year
        self.colour = colour
        self.service_notes = service_notes
    
  
    def option_model(self): 
        if self.option == 'sport':
            print(f'{self.name} wants a sport model')
        else:
            print(f'{self.name} wants a wants a standard model')
        
 
car_1 = Car('Alice', 'Ford', 'Fiesta', 'sport', '2016', 'yellow', 'yes')

car_1.option_model() 
car_2 = Car('Alice', 'Ford', 'Fiesta', 'GTI', '2016', 'yellow', 'yes')        
car_2.option_model() 

          
```

    Alice wants a sport model
    Alice wants a wants a standard model
    


```python
class Car:
    def __init__(self, name, manufacturer, model, option, year, colour, service_notes):
        self.name = name
        self.manufacturer = manufacturer
        self.model = model
        self.option = option
        self.year = year
        self.colour = colour
        self.service_notes = service_notes

    def car_colour(self):
        choose_colour = ['white','black','blue']
        if self.colour in choose_colour:
            print(f'{self.name} wants a {self.colour} car')
        else:
            print(f'{self.name}, {self.colour} is not available')

car_2 = Car('Alice', 'Ford', 'Fiesta', 'GTI', '2016', 'yellow', 'yes')
car_2.car_colour()
car_3 = Car('Alice', 'Ford', 'Fiesta', 'GTI', '2016', 'black', 'yes')
car_3.car_colour()

     
```

    Alice, yellow is not available
    Alice wants a black car
    


```python
class Car:
    def __init__(self, name, manufacturer, model, option, year, colour, service_notes):
        self.name = name
        self.manufacturer = manufacturer
        self.model = model
        self.option = option
        self.year = year
        self.colour = colour
        self.service_notes = service_notes


    def order(self):
        order_details = [self.name, self.manufacturer, self.model, self.year, self.colour, self.service_notes]
        return order_details

car_4 = Car('Charlie', 'Ford', 'Fiesta', 'blue', '2016', 'Yellow', 'Yes')
car_4.order()


```




    ['Charlie', 'Ford', 'Fiesta', '2016', 'Yellow', 'Yes']




```python
class Car:
    def __init__(self, name, manufacturer, model, option, year, colour, service_notes):
        self.name = name
        self.manufacturer = manufacturer
        self.model = model
        self.option = option
        self.year = year
        self.colour = colour
        self.service_notes = service_notes
        
    def service_list(self, service_notes):
        result = []
        current_record = {}
        
        for line in service_notes:
            line = line.strip()
            if line.startswith('Customer'): 
                current_record['Customer'] = line.split(' ',1)[1]
            elif line.startswith('Car'):
                current_record['Car']= line.split(' ',1)[1]
            elif line.startswith('Service'):
                current_record['Service'] = line.split(' ',1)[1]
                result.append(current_record)
                current_record = {}
                
        return result
            
                    
service_notes = ['Customer AliceJenkins\n',
                         'Car Honda\n',
                         'Service Fifty_Thousand\n','Customer BobElliot\n',
                         'Car Totota, Rav4, Silver, 2018\n',
                         'Service Thirty_Thousand,\n',
                         'Customer CharlieWallace\n',
                         'Car Ford\n',
                         'Service Ten_Thousand\n']

car_5 = Car('Charlie', 'Ford', 'Fiesta', 'blue', '2016', 'Yellow', 'Yes')
Service_details = car_5.service_list(service_notes)
print(Service_details)
                
           
```

    [{'Customer': 'AliceJenkins', 'Car': 'Honda', 'Service': 'Fifty_Thousand'}, {'Customer': 'BobElliot', 'Car': 'Totota, Rav4, Silver, 2018', 'Service': 'Thirty_Thousand,'}, {'Customer': 'CharlieWallace', 'Car': 'Ford', 'Service': 'Ten_Thousand'}]
    


```python
class Car:
    def __init__(self, name, manufacturer, model, year, colour, option, service_notes):
        self.name = name
        self.manufacturer = manufacturer
        self.model = model
        self.year = year
        self.colour = colour
        self.option = option
        self.service_notes = service_notes

    def order(self):
        return [self.name, self.manufacturer, self.model, self.year, self.colour, self.option,self.service_notes]


    def service_list(self):
        service_records = [
                {'Customer': 'AliceJenkins', 'Car': 'Honda', 'Service': 'Fifty_Thousand'},
                {'Customer': 'BobElliot', 'Car': 'Totota,', 'Service': 'Thirty_Thousand,'},
                {'Customer': 'CharlieWallace', 'Car': 'Ford', 'Service': 'Ten_Thousand'}
        ]
        return service_records


class Orders:
    def __init__ (self):
        self.orders_list = []

    
        
    def order(self, car):
        if isinstance(car, Car):
            self.orders_list.append(car)
            print(f"Order for {car.name} was added successfully")
        else:
            print("car doesn't exist. Please enter car details")
                
    def cancel(self, car):
        if car in self.orders_list:
            self.orders_list.remove(car)
            print(f"Order for {car.name} has been cancelled")
        else:
            print(f"No order found {car.name} to cancel")
            
    def delivered(self, car):
        if car in self.orders_list:
            self.orders_list.remove(car)
            print(f"Order for {car.name} has been delivered")
        else:
            print(f"No order found for {car.name} to mark delivered")
            
    def display_orders(self):
        if not self.orders_list:
            print("No orders are pending")
        else:
            for idx, car in enumerate(self.orders_list, start=1):
                print(f"Order {idx}:{car.order()}")
    def customer_names(self):
        return [car.name for car in self.orders_list]


service_notes = "Standard Service" 
car_x = Car('None', 'None', 'None', 'None', 'None', 'None', service_notes)

  #Step 4      
car_1 = Car('Alice', 'Honda', 'CRV', '2020', 'Blue', 'sport', service_notes)
car_2 = Car('Bob', 'Toyota', 'Rav4', '2022', 'Green', 'No', service_notes)
car_3 = Car('Charlie', 'Ford', 'Fiesta', '2016', 'Yellow', 'Yes', service_notes)


# Step 8
order_1 = Orders()

# Step 9
order_1.order(car_1)
order_1.order(car_2)
order_1.order(car_3)

# Step 10
print("\n----Step 10-------")
print(sorted(order_1.customer_names()))

print("\n-----------")

# Step 11
order_1.delivered(car_2)
print("\n---Step 11 - Orders after Delivery----")
print(sorted(order_1.customer_names()))


# Step 12
order_1.cancel(car_1)
print("\n---Step 12 - Orders after cancellation----")
print(order_1.customer_names())

print("\n-----------")


#Step 5
print("\n---display Step 5----")

array = car_3.order()
print(array)

# Step 6
print("\n----Step 6-------")
print(f' {car_2.name} is {car_2.colour}')

# Step 7
print("\n----Step 7-------")
print(f' {car_1.name} is {car_1.model}')

print("\n Step 8 - order_1 = Orders() is already instantiated in this example")

# Step 15
print("\n----Step 15-------")

print(car_x.service_list())

```

    Order for Alice was added successfully
    Order for Bob was added successfully
    Order for Charlie was added successfully
    
    ----Step 10-------
    ['Alice', 'Bob', 'Charlie']
    
    -----------
    Order for Bob has been delivered
    
    ---Step 11 - Orders after Delivery----
    ['Alice', 'Charlie']
    Order for Alice has been cancelled
    
    ---Step 12 - Orders after cancellation----
    ['Charlie']
    
    -----------
    
    ---display Step 5----
    ['Charlie', 'Ford', 'Fiesta', '2016', 'Yellow', 'Yes', 'Standard Service']
    
    ----Step 6-------
     Bob is Green
    
    ----Step 7-------
     Alice is CRV
    
     Step 8 - order_1 = Orders() is already instantiated in this example
    
    ----Step 15-------
    [{'Customer': 'AliceJenkins', 'Car': 'Honda', 'Service': 'Fifty_Thousand'}, {'Customer': 'BobElliot', 'Car': 'Totota,', 'Service': 'Thirty_Thousand,'}, {'Customer': 'CharlieWallace', 'Car': 'Ford', 'Service': 'Ten_Thousand'}]
    


```python

```


```python

```


```python

```
