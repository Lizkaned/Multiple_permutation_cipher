# Multiple_permutation_cipher
def encrypt(text: str, col_key: str, row_key: str):
    result: list = [''] * (len(col_key) * len(row_key))

    for i in range(0, len(row_key)):
        for j in range(0, len(col_key)):
            new_row_i = int(row_key[i])
            new_col_i = int(col_key[j])
            result[(new_col_i - 1) * len(row_key) + (new_row_i - 1)] = text[i *
                                                                            len(col_key) + j] if i * len(col_key) + j < len(text) else '_'
    return ''.join(result)

def decrypt(text: str, col_key: str, row_key: str):
    result: list = [''] * (len(col_key) * len(row_key))

    for i in range(0, len(row_key)):
        for j in range(0, len(col_key)):
            new_row_i = int(row_key[i])
            new_col_i = int(col_key[j])
            result[i * len(col_key) + j] = text[(new_col_i - 1) * len(row_key) + (new_row_i - 1)
                                                ] if (new_col_i - 1) * len(row_key) + (new_row_i - 1) < len(text) else ''
    return ''.join(result)

text: str = input('Введіть текст: ')
col_key: str = input('Введіть порядок перестановки стовпчиків: ')
row_key: str = input('Введіть порядок перестановки рядків: ')
encrypted: str = encrypt(text, col_key, row_key)
print("Зашифрований текст: ", encrypted)
print("Розшифрований текст: ", decrypt(encrypted, col_key, row_key))
