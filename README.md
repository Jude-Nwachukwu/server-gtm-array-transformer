# Server-Side GTM Array Attribute Transformer

## 📌 Overview
The **Server-Side GTM Array Attribute Transformer** is a Google Tag Manager (GTM) **variable custom template** designed for server-side implementations. It extracts values from a specified **attribute key** in an array of objects from **event data** and transforms them into an array of **strings, integers, or numbers**.

**📢 Here is the custom template repository for the [web GTM custom template](https://github.com/Jude-Nwachukwu/gtm-array-attribute-transformer)**


### ✅ Features:
- Supports **GA4 Ecommerce Items Array** from **event data** (`getEventData('items')`).
- Allows **custom variables** containing an array of objects.
- Enables **automatic type conversion** (String, Integer, Number).
- Implements **error handling** for invalid inputs.

Developed by **Jude Nwachukwu Onyejekwe** for [**DumbData**](https://dumbdata.co/). Find more analytics resources in the **Measurement Resource Hub**.

---

## ⚙️ Configuration

### **Fields Tab Settings**
| Field Name                  | Type     | Description |
|-----------------------------|----------|-------------|
| `Ecommerce Items Array Source` | Select | Choose the source of the array (`GA4 Ecommerce Items Request` or `Custom Variable`). |
| `Items Array Variable` | Text | The variable containing the array of objects (enabled for `Custom Variable` source). |
| `The Attribute Key` | Text | The attribute key whose values will be extracted from each object. |
| `Array Value Format Type` | Radio | Select how the extracted values should be formatted (`String`, `Integer`, `Number`). |

---

## 🚀 How It Works
1. The template retrieves the **items array** from either:
   - The **Event Data** (`getEventData('items')`) if `GA4 Ecommerce Items Request` is selected.
   - A **Custom Variable** if `Custom Variable` is selected.
2. It validates that the retrieved value is **an array**.
3. It extracts values from the specified **attribute key**.
4. It **transforms** the values into **strings, integers, or numbers** based on the selected format.
5. It handles **errors** gracefully:
   - If the input is **not an array**, it returns `['']`.
   - If the attribute key **doesn't exist**, it returns `['']`.
   - If a string **cannot be converted** to a number, it returns the original string.

---

## 🔍 Examples

| **Input Array** | **Config: Attribute Key** | **Config: Output Type** | **Output** |
|---------------|----------------------|---------------------|--------|
| `[ {"item_id": "9bdd2"}, {"item_id": "xyz123"} ]` | `item_id` | `String` | `['9bdd2', 'xyz123']` |
| `[ {"price": "44.00"}, {"price": "29.99"} ]` | `price` | `Number` | `[44.00, 29.99]` |
| `[ {"index": "3"}, {"index": "7"} ]` | `index` | `Integer` | `[3, 7]` |
| `[ {"name": "Shirt"}, {"name": "Pants"} ]` | `name` | `String` | `['Shirt', 'Pants']` |
| `[ {"id": "XYZ"}, {"id": "ABC"} ]` | `non_existent_key` | `String` | `['', '']` |
| `not_an_array` | `name` | `String` | `['']` |
| `[ {"price": "not_a_number"}, {"price": "50.5"} ]` | `price` | `Number` | `['not_a_number', 50.5]` |
| `[ {"id": "123", "name": "Item A", "price": "10.99"}, {"id": "456", "name": "Item B", "price": "20.50"} ]` | `name` | `String` | `['Item A', 'Item B']` |

---

## 📖 How to Use
1. **Go to GTM** → **Variables** → **New**.
2. Select **"Custom Template"** and **import** the template.
3. Configure the **Fields Tab** based on your data source.
4. Save and use this variable in tags, triggers, or other variables.

---

## 📌 Notes
- **Ensure your server-side GTM setup is correctly configured** before using this template.
- **Handle missing keys** by setting a default fallback in GTM triggers or conditions.
- **Use the correct data type** for better compatibility with analytics and tracking tools.

---

## 📜 License
This template is released under the **APACHE License**. Feel free to contribute and improve!
