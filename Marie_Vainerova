import math

class Locality:
  def __init__(self, name, coefficient = 1):
    self.name = name
    self.coefficient = coefficient
class Property:
  def __init__(self, locality):
    self.locality = locality
class Estate(Property):
  def __init__(self, locality, estate_type, area):
    super().__init__(locality)
    self.estate_type = estate_type
    self.area = area
#land (zemědělský pozemek) má koeficient 0.85.
#building site (stavební pozemek) má koeficient 9.
#forrest (les) má koeficient 0.35.
  def calculate_tax(self):
    if self.estate_type == 'land':
      return math.ceil(self.area * 0.85 * self.locality.coefficient)
    if self.estate_type == 'building site':
      return math.ceil(self.area * 9 * self.locality.coefficient)
    if self.estate_type == 'forrest':
      return math.ceil(self.area * 0.35 * self.locality.coefficient)
    else:
      print('Unknown etate type.')
  def __str__(self):
    if self.estate_type == 'land':
      return f'Zemědělský pozemek, lokalita {self.locality.name} (koeficient {self.locality.coefficient}), {self.area} metrů čtverečních, daň {self.calculate_tax()} Kč.'
    if self.estate_type == 'building site':
      return f'Stavební pozemek, lokalita {self.locality.name} (koeficient {self.locality.coefficient}), {self.area} metrů čtverečních, daň {self.calculate_tax()} Kč.'
    if self.estate_type == 'forrest':
      return f'Les, lokalita {self.locality.name} (koeficient {self.locality.coefficient}), {self.area} metrů čtverečních, daň {self.calculate_tax()} Kč.'
class Residence(Property):
  def __init__(self, locality, area, commercial=False):
    super().__init__(locality)
    self.area = area
    self.commercial = commercial
  def calculate_tax(self):
    if self.commercial == True:
      return self.area * self.locality.coefficient * 15 * 2
    else:
      return self.area * self.locality.coefficient * 15
  def __str__(self):
    if self.commercial == True:
      return f'Dům nebo byt, vhodný ke komerčnímu vzužití, lokalita {self.locality.name} (koeficient {self.locality.coefficient}), {self.area} metrů čtverečních, daň {self.calculate_tax()} Kč.'
    else:
      return f'Dům nebo byt, lokalita {self.locality.name} (koeficient {self.locality.coefficient}), {self.area} metrů čtverečních, daň {self.calculate_tax()} Kč.'

Brno = Locality('Brno', 3)
Manetin = Locality('Manětín', 0.8)
pozemek = Estate(Brno, 'building site', 100)
byt = Residence(Brno, 50, False)
zem_poz = Estate(Manetin, 'land', 900)
dum = Residence(Manetin, 120)
kancelar = Residence(Brno, 90, True)
print(kancelar.calculate_tax())
print(kancelar)
'''
Zemědělský pozemek o ploše 900 metrů čtverečních v lokalitě Manětín s koeficientem 0.8. Daň z této nemovitosti je 900 * 0.85 * 0.8 = 612.
Dům s podlahovou plochou 120 metrů čtverečních v lokalitě Manětín s koeficientem 0.8. Daň z této nemovitosti je 120 * 0.8 * 15 = 1440.
Kancelář (tj. komerční nemovitost) s podlahovou plochou 90 metrů čtverečních v lokalitě Brno s koeficientem 3. Daň z této nemovitosti je 90 * 3 * 15 * 2 = 8100.
'''
