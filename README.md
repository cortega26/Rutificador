[![Python](https://img.shields.io/badge/Python-3.6%2B-blue)](https://www.python.org/)
[![License](https://img.shields.io/badge/License-MIT-green.svg)](LICENSE)
[![Code Style](https://img.shields.io/badge/code%20style-black-000000.svg)](https://github.com/psf/black)

# Rutificador

Una biblioteca Python para validar y formatear RUTs (Rol Único Tributario) chilenos.

## Características

- Validación del formato del RUT.
- Cálculo del dígito verificador del RUT.
- Formateo del RUT con diferentes opciones (separador de miles, mayúsculas, formato de salida).
- Validación y formateo de listas de RUTs.
- Manejo de excepciones personalizadas.

## Instalación

Puedes instalar la librería utilizando pip:

```python
!pip install *****
```

## Uso

### Importar la clase Rut

```python
from ***** import Rut
```

## Crear Un Objeto

```python
rut1 = Rut('12345678-5')
rut2 = Rut('12345670-k')
```

## Validar un RUT

La validación del RUT se realiza automáticamente al crear un objeto `Rut`. Si el RUT ingresado no es válido, se lanzará una excepción `RutInvalidoError`.

## Calcular el Dígito Verificador de un RUT

```python
from ***** import RutDigitoVerificador

digito_verificador = RutDigitoVerificador('12345678').digito_verificador
print(digito_verificador)  # Salida: 5
```

## Formatear un RUT

```python
# Formato predeterminado
print(rut1.formatear())  # Salida: 12345678-9

# Con separador de miles
print(rut1.formatear(separador_miles=True))  # Salida: 12.345.678-9

# En mayúsculas
print(rut2.formatear(mayusculas=True))  # Salida: 12345670-K

# Con separador de miles y en mayúsculas
print(rut2.formatear(separador_miles=True, mayusculas=True))  # Salida: 12.345.670-K
```

## Validar y Formatear una lista de RUTs con y sin formato

```python
# Sin formato
ruts = ['12345678-5', '12345670-k', '98765432-1']
ruts_validos = Rut.validar_lista_ruts(ruts)
print(Rut.formatear_lista_ruts(ruts_validos, separador_miles=True, mayusculas=True))
# Salida: [12.345.678-5, 12.345.670-K, 98.765.432-1]
# En caso de que hayan RUTs inválidos, el método validar_lista_ruts creará dos listas:
# una con los RUTs válidos (en el formato especificado) y otra con los inválidos.


# En formato csv
ruts = ['12.345.678', '9876543', '1.234.567-4', '18005183']
csv_ruts = Rut.formatear_lista_ruts(ruts, formato='csv')
print(csv_ruts)
# Salida
rut
12345678-5
9876543-3
1234567-4
18005183-k

# En formato json
ruts = ['12.345.678', '9876543', '1.234.567-4', '18005183']
json_ruts = Rut.formatear_lista_ruts(ruts, formato='json')
print(json_ruts)
# Salida
[{"rut": "12345678-5"}, {"rut": "9876543-3"}, {"rut": "1234567-4"}, {"rut": "18005183-k"}]

# En formato xml
ruts = ['12.345.678', '9876543', '1.234.567-4', '18005183']
xml_ruts = Rut.formatear_lista_ruts(ruts, formato='xml')
print(xml_ruts)
# Salida
<root>
    <rut>12345678-5</rut>
    <rut>9876543-3</rut>
    <rut>1234567-4</rut>
    <rut>18005183-k</rut>
</root>
```

## Contribuciones

Las contribuciones son bienvenidas. Por favor, sigue las pautas de contribución descritas en el archivo CONTRIBUTING.md.

## Licencia

Este proyecto está licenciado bajo la Licencia MIT.

## Créditos

Este paquete fue creado por Carlos Ortega y se inspiró en el proyecto [rut-chile](https://github.com/gevalenz/rut-chile) de [gevalenz](https://github.com/gevalenz), que es un módulo Python que proporciona funcionalidades comunes relacionadas con el RUT chileno.
