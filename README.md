import random

Choice = "+-/*!&$#?=@abcdefghijklnopqrstuvwxyzABCDEFGHIJKLMNOPQRSTUVWXYZ1234567890"
length = int(input("Введите длинну пароля"))

password = ""
for i in range(length):
    Choice += random.choice(Choice)

print(password)
