- 👋 Hi, I’m @HAWKEYW0
- 👀 I’m interested in ...
- 🌱 I’m currently learning ...
- 💞️ I’m looking to collaborate on ...
- 📫 How to reach me ...
- 😄 Pronouns: ...
- ⚡ Fun fact: ...

<!---
HAWKEYW0/HAWKEYW0 is a ✨ special ✨ repository because its `README.md` (this file) appears on your GitHub profile.
You can click the Preview link to take a look at your changes.
--->
import random

class Character:
    def __init__(self, name, health, attack, defense):
        self.name = name
        self.health = health
        self.attack = attack
        self.defense = defense

    def take_damage(self, damage):
        damage_taken = max(0, damage - self.defense)
        self.health -= damage_taken
        return damage_taken

    def is_alive(self):
        return self.health > 0

def battle(character1, character2):
    while character1.is_alive() and character2.is_alive():
        # Karakter 1 saldırıyor
        damage_to_char2 = character1.attack + random.randint(-5, 5)
        damage_taken_by_char2 = character2.take_damage(damage_to_char2)
        print(f"{character1.name} attacked {character2.name} for {damage_taken_by_char2} damage!")

        if not character2.is_alive():
            print(f"{character2.name} has been defeated!")
            break

        # Karakter 2 saldırıyor
        damage_to_char1 = character2.attack + random.randint(-5, 5)
        damage_taken_by_char1 = character1.take_damage(damage_to_char1)
        print(f"{character2.name} attacked {character1.name} for {damage_taken_by_char1} damage!")

        if not character1.is_alive():
            print(f"{character1.name} has been defeated!")

# Örnek karakterler oluşturma
hero = Character("Hero", health=100, attack=20, defense=5)
enemy = Character("Enemy", health=80, attack=15, defense=3)

# Savaşı başlat
battle(hero, enemy)
