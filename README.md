class HashTable:
    def __init__(self, size):
        self.size = size
        self.table = [None] * size
        self.comparisons = 0

    def hash(self, key):
        # Simple hash function
        return hash(key) % self.size

    def insert(self, key, value):
        index = self.hash(key)
        if self.table[index] is None:
            self.table[index] = (key, value)
        else:
            print(f"Collision at index {index} for key {key}")

    def search(self, key):
        index = self.hash(key)

        while self.table[index] is not None:
            self.comparisons += 1
            if self.table[index][0] == key:

                return self.table[index][1]  # Return the value (phone number)
            else:
                print(key,"not found")
                break

    def get_comparisons(self):
        return self.comparisons

    def __str__(self):
        result = ""
        for i in range(self.size):
            result += f"[{i}]: {self.table[i]}\n"
        return result


# Example usage
phone_book = HashTable(5)

# Insert client data
phone_book.insert(11, "XYZ")
phone_book.insert(24, "ABC")
phone_book.insert(36, "PQR")
phone_book.insert(34, "MNP")
phone_book.insert(33, "JKL")

# Search for phone numbers
print("name of no 11 is ",phone_book.search(11))
#print(phone_book.search(24))
#print(phone_book.search(99))
search_numbers = [24, 34, 33]
for number in search_numbers:
    phone_book.search(number)

# Get the number of comparisons
print(f"Total comparisons made: {phone_book.get_comparisons()}")
# Print the entire hash table
print(phone_book)
