# На вход программе подается строка текста на английском языке, в которой нужно зашифровать все слова. 
# Каждое слово строки следует зашифровать с помощью шифра Цезаря (циклического сдвига на длину этого слова). 
# Строчные буквы при этом остаются строчными, а прописные – прописными.
text, s, cipher_txt = input() + ' ', '', ''
en_language_lower, en_language_upper = 'abcdefghijklmnopqrstuvwxyz', 'ABCDEFGHIJKLMNOPQRSTUVWXYZ'
for k in range(len(text)):
    if text[k].isalpha():
        s += text[k]
    else:
        n = len(s)
        s += text[k]
        for i in range(len(s)):
            if s[i] in en_language_upper:
                for j in range(len(en_language_upper)):
                    if s[i] == en_language_upper[j]:
                        if j+n >= len(en_language_upper):
                            x = len(en_language_upper) - j
                            y = n - x
                            cipher_txt += en_language_upper[y]
                        else:
                            cipher_txt += en_language_upper[j+n]
                            
            elif s[i] in en_language_lower:
                for j in range(len(en_language_lower)):
                    if s[i] == en_language_lower[j]:
                        if j+n >= len(en_language_lower):
                            x = len(en_language_lower) - j
                            y = n - x
                            cipher_txt += en_language_lower[y]
                        else:
                            cipher_txt += en_language_lower[j+n]
            else:
                cipher_txt += s[i]
        s = ''
print(cipher_txt.rstrip())
