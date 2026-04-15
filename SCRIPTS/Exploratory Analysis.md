## Histograms


```python
#import packages
import pandas as pd
import matplotlib.pyplot as plt
```


```python
# Healthy = 1, Unhealthy = 0

healthy = [
    "Apple", "Avocado", "Banana", "Beef", "Beef-Fillet", "Beef-Goulash",
    "Beef-Patty", "Blueberry-Yogurt", "Grapes", "Grilled-Chicken-Salad",
    "Grilled-Pizza", "Ground-Beef", "Honey", "Jackfruit", "Kiwi",
    "Lemon", "Lime", "Lychees", "Mango", "Milk", "Mint", "Mozzarella",
    "Orange", "Pancake", "Papaya", "Parsley", "Passion-Fruit",
    "Peach", "Pear", "Pineapple", "Plum", "Raspberries", "Sandwich",
    "Strawberries", "Tangerine", "Watermelon", "Yogurt",
    "American-Cheese", "Blueberry-Yogurt"
]

unhealthy = [
    "BBQ-Chicken-Pizza", "BBQ-Pizza", "Beef-Pizza", "Beef-Ribs",
    "Beef-Steak", "Biscuit", "Cheese-Pizza", "Chicken-Pizza",
    "Cupcake", "Donut", "Double-Cheeseburger", "Egg-Roll",
    "Hot-Chocoloate", "Hot-Dog", "Mayonnaise", "Muffin",
    "Mustard", "Pie", "Sausage-Pizza", "Seafood-Pizza",
    "Vanilla-Yogurt", "Vegetable-Pizza", "Vegetarian-Pizza",
    "Waffles", "Zinger-Burger", "Chocolate-Yogurt", "Strawberry-Jam"
]
```


```python
print(healthy)
```

    ['Apple', 'Avocado', 'Banana', 'Beef', 'Beef-Fillet', 'Beef-Goulash', 'Beef-Patty', 'Blueberry-Yogurt', 'Grapes', 'Grilled-Chicken-Salad', 'Grilled-Pizza', 'Ground-Beef', 'Honey', 'Jackfruit', 'Kiwi', 'Lemon', 'Lime', 'Lychees', 'Mango', 'Milk', 'Mint', 'Mozzarella', 'Orange', 'Pancake', 'Papaya', 'Parsley', 'Passion-Fruit', 'Peach', 'Pear', 'Pineapple', 'Plum', 'Raspberries', 'Sandwich', 'Strawberries', 'Tangerine', 'Watermelon', 'Yogurt', 'American-Cheese', 'Blueberry-Yogurt']



```python
print(unhealthy)
```

    ['BBQ-Chicken-Pizza', 'BBQ-Pizza', 'Beef-Pizza', 'Beef-Ribs', 'Beef-Steak', 'Biscuit', 'Cheese-Pizza', 'Chicken-Pizza', 'Cupcake', 'Donut', 'Double-Cheeseburger', 'Egg-Roll', 'Hot-Chocoloate', 'Hot-Dog', 'Mayonnaise', 'Muffin', 'Mustard', 'Pie', 'Sausage-Pizza', 'Seafood-Pizza', 'Vanilla-Yogurt', 'Vegetable-Pizza', 'Vegetarian-Pizza', 'Waffles', 'Zinger-Burger', 'Chocolate-Yogurt', 'Strawberry-Jam']



```python
data = []
# healthy
for food in healthy:
    data.append({"Food": food, "Label": 1})
# unhealthy
for food in unhealthy:
    data.append({"Food": food, "Label": 0})

df = pd.DataFrame(data)
print(df.head())
```

              Food  Label
    0        Apple      1
    1      Avocado      1
    2       Banana      1
    3         Beef      1
    4  Beef-Fillet      1



```python
counts = df["Label"].value_counts().sort_index()

# Store the returned bar container in the 'bars' variable
bars = plt.bar(["Unhealthy (0)", "Healthy (1)"], counts)
plt.title("Food Category Counts")
plt.xlabel("Category")
plt.ylabel("Number of Items")

# Now 'bars' is defined and can be used in the loop
for bar in bars:
    height = bar.get_height()
    plt.text(bar.get_x() + bar.get_width() / 2, height,
             str(height),
             ha='center', va='bottom', fontsize=11)
plt.show()
```


    
![png](output_6_0.png)
    



```python
import os

base_path = "Nutrition Food Proj_Cleaned"  # change this to your folder path

food_counts = {}

for food in os.listdir(base_path):
    folder_path = os.path.join(base_path, food)
    
    if os.path.isdir(folder_path):
        num_images = len([
            f for f in os.listdir(folder_path)
            if f.lower().endswith(('.png', '.jpg', '.jpeg'))
        ])
        food_counts[food] = num_images
```


```python
food_counts = {k: v for k, v in food_counts.items() if not k.startswith(".")}
```


```python
import matplotlib.pyplot as plt

# Sort by count (important!)
sorted_items = sorted(food_counts.items(), key=lambda x: x[1])
foods, counts = zip(*sorted_items)

plt.figure(figsize=(10, 12))
bars = plt.barh(foods, counts)

plt.title("Number of Images per Food Folder")
plt.xlabel("Number of Images")

# Add labels
for bar in bars:
    width = bar.get_width()
    plt.text(width, bar.get_y() + bar.get_height()/2,
             str(width), va='center')

plt.tight_layout()
plt.show()
```


    
![png](output_9_0.png)
    



```python
plt.figure(figsize=(8, 5))
plt.hist(list(food_counts.values()), bins=10)

plt.title("Distribution of Images per Folder")
plt.xlabel("Number of Images")
plt.ylabel("Number of Folders")

plt.show()
```


    
![png](output_10_0.png)
    



```python

```
