# Refatoração de Data Clumps

Os Data Clumps são uma anomalia de código comum em programação que ocorre quando um grupo de variáveis frequentemente aparece junto em múltiplos locais do código. Isso geralmente indica que essas variáveis deveriam ser encapsuladas em uma única estrutura de dados, como uma classe ou um objeto. Essa prática pode melhorar a manutenibilidade, a legibilidade e a reutilização do código, além de evitar potenciais problemas de desempenho.

## Código Original (Antes da Refatoração)

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
send_invoice("John Doe", "123 Elm St", "Springfield", "IL", "62701")
