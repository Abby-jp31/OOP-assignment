# OOP-assignment
class Superhero:
    def __init__(self, name, secret_identity, powers, origin_story):
        self.name = name
        self._secret_identity = secret_identity  # Encapsulated attribute
        self.powers = powers
        self.origin_story = origin_story
        self.health = 100
        self.energy = 100
    
    def introduce(self):
        print(f"Hero Name: {self.name}")
        print(f"Powers: {', '.join(self.powers)}")
        print(f"Origin: {self.origin_story}")
    
    def use_power(self, power_index):
        if power_index < len(self.powers):
            print(f"{self.name} uses {self.powers[power_index]}!")
            self.energy -= 10
        else:
            print("Power not available!")
    
    def get_secret_identity(self):
        return self._secret_identity
    
    def set_secret_identity(self, new_identity):
        print(f"Changing secret identity from {self._secret_identity} to {new_identity}")
        self._secret_identity = new_identity
    
    def rest(self):
        self.energy = min(100, self.energy + 30)
        self.health = min(100, self.health + 10)
        print(f"{self.name} rests and recovers some energy and health.")

class CosmicSuperhero(Superhero):
    def __init__(self, name, secret_identity, powers, origin_story, home_planet):
        super().__init__(name, secret_identity, powers, origin_story)
        self.home_planet = home_planet
        self.cosmic_energy = 150  # Cosmic heroes have more energy
    
    def use_power(self, power_index):  # Overriding the parent method
        if power_index < len(self.powers):
            print(f"{self.name} channels cosmic energy to use {self.powers[power_index]}! 🌌")
            self.cosmic_energy -= 15
        else:
            print("Power not available!")
    
    def rest(self):  # Overriding with cosmic-specific rest
        self.cosmic_energy = min(200, self.cosmic_energy + 50)
        self.health = min(100, self.health + 15)
        print(f"{self.name} meditates under the stars and absorbs cosmic energy. ✨")


batman = Superhero(
    name="Batman",
    secret_identity="Bruce Wayne",
    powers=["Martial Arts", "Detective Skills", "High-Tech Gadgets"],
    origin_story="Witnessed his parents' murder as a child and vowed to fight crime."
)

silver_surfer = CosmicSuperhero(
    name="Silver Surfer",
    secret_identity="Norrin Radd",
    powers=["Cosmic Power", "Flight", "Energy Manipulation"],
    origin_story="Former astronomer who sacrificed himself to save his planet.",
    home_planet="Zenn-La"

batman.introduce()
batman.use_power(1)
print()

silver_surfer.introduce()
print(f"Home Planet: {silver_surfer.home_planet}")
silver_surfer.use_power(0)
silver_surfer.rest()
POLYMORPHISM CHALLENGE.
class Animal:
    def __init__(self, name):
        self.name = name
    
    def move(self):
        raise NotImplementedError("Subclasses must implement this method")
    
    def describe(self):
        print(f"I am a {self.name}.")

class Bird(Animal):
    def move(self):
        print(f"{self.name} is flying! 🕊️")

class Fish(Animal):
    def move(self):
        print(f"{self.name} is swimming! 🐟")

class Snake(Animal):
    def move(self):
        print(f"{self.name} is slithering! 🐍")

class Horse(Animal):
    def move(self):
        print(f"{self.name} is galloping! 🐎")

Create a list of different animals
animals = [
    Bird("Eagle"),
    Fish("Salmon"),
    Snake("Python"),
    Horse("Mustang")
]

 Demonstrate polymorphism
for animal in animals:
    animal.describe()
    animal.move()
    print()  # Add empty line between animal
