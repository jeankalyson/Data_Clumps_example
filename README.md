# Refatoração de Data Clumps

Os Data Clumps são uma anomalia de código comum em programação que ocorre quando um grupo de variáveis frequentemente aparece junto em múltiplos locais do código. Isso geralmente indica que essas variáveis deveriam ser encapsuladas em uma única estrutura de dados, como uma classe ou um objeto. Essa prática pode melhorar a manutenibilidade, a legibilidade e a reutilização do código, além de evitar potenciais problemas de desempenho.

## Código Original

```python
def process_payment(name, address, city, state, zipcode, card_number, card_expiry, card_cvv):
    # processamento do pagamento
    print(f"Processing payment for {name}")
    print(f"Billing address: {address}, {city}, {state}, {zipcode}")
    print(f"Card details: {card_number}, Expiry: {card_expiry}, CVV: {card_cvv}")

def send_invoice(name, address, city, state, zipcode):
    # envio de fatura
    print(f"Sending invoice to {name}")
    print(f"Address: {address}, {city}, {state}, {zipcode}")

# Chamadas de função
process_payment("John Doe", "123 Elm St", "Springfield", "IL", "62701", "1234567812345678", "12/25", "123")
send_invoice("John Doe", "123 Elm St", "Springfield", "IL", "62701")```

A refatoração envolve encapsular as variáveis recorrentes em classes, resultando em um código mais organizado e legível. Aqui, as informações do cliente são encapsuladas na classe Customer, e os dados do cartão de crédito na classe CreditCard:

# Código Refatorado
```python
class Customer:
    def __init__(self, name, address, city, state, zipcode):
        self.name = name
        self.address = address
        self.city = city
        self.state = state
        self.zipcode = zipcode

class CreditCard:
    def __init__(self, number, expiry, cvv):
        self.number = number
        self.expiry = expiry
        self.cvv = cvv

def process_payment(customer, credit_card):
    # processamento do pagamento
    print(f"Processing payment for {customer.name}")
    print(f"Billing address: {customer.address}, {customer.city}, {customer.state}, {customer.zipcode}")
    print(f"Card details: {credit_card.number}, Expiry: {credit_card.expiry}, CVV: {credit_card.cvv}")

def send_invoice(customer):
    # envio de fatura
    print(f"Sending invoice to {customer.name}")
    print(f"Address: {customer.address}, {customer.city}, {customer.state}, {customer.zipcode}")

# Criando objetos
customer = Customer("John Doe", "123 Elm St", "Springfield", "IL", "62701")
credit_card = CreditCard("1234567812345678", "12/25", "123")

# Chamadas de função
process_payment(customer, credit_card)
send_invoice(customer)
```

# Código Refatorado
A refatoração envolve encapsular as variáveis recorrentes em classes, resultando em um código mais organizado e legível.  Logo, a seguir, as informações do cliente são encapsuladas na classe Customer, e os dados do cartão de crédito na classe CreditCard:
```python
class Customer:
    def __init__(self, name, address, city, state, zipcode):
        self.name = name
        self.address = address
        self.city = city
        self.state = state
        self.zipcode = zipcode

class CreditCard:
    def __init__(self, number, expiry, cvv):
        self.number = number
        self.expiry = expiry
        self.cvv = cvv

def process_payment(customer, credit_card):
    # processamento do pagamento
    print(f"Processing payment for {customer.name}")
    print(f"Billing address: {customer.address}, {customer.city}, {customer.state}, {customer.zipcode}")
    print(f"Card details: {credit_card.number}, Expiry: {credit_card.expiry}, CVV: {credit_card.cvv}")

def send_invoice(customer):
    # envio de fatura
    print(f"Sending invoice to {customer.name}")
    print(f"Address: {customer.address}, {customer.city}, {customer.state}, {customer.zipcode}")

# Criando objetos
customer = Customer("John Doe", "123 Elm St", "Springfield", "IL", "62701")
credit_card = CreditCard("1234567812345678", "12/25", "123")

# Chamadas de função
process_payment(customer, credit_card)
send_invoice(customer)

```
Ao refatorar o código para encapsular as informações do cliente e do cartão de crédito em classes, o código torna-se mais organizado e legível. A classe Customer agrupa as informações do cliente, enquanto a classe CreditCard agrupa os dados do cartão de crédito. As funções process_payment e send_invoice agora aceitam objetos dessas classes como parâmetros, o que reduz a repetição de variáveis e melhora a clareza do código. Isso facilita a manutenção e a extensão do código no futuro, além de reduzir a duplicação e a probabilidade de erros.


