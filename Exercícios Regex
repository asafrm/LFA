# Resolução completa exercícios regex aula 08/09 — Expressões Regulares

## 1. Palavras sobre `{0,1}` que terminam em `00`

### Linguagem

Considere o alfabeto:

```text
Σ = {0,1}
```

A linguagem é formada por todas as palavras binárias que terminam exatamente com os símbolos `00`.

Formalmente:

```text
L = { w ∈ {0,1}* | w termina em 00 }
```

### Expressão regular

```regex
^[01]*00$
```

### Justificativa

- `^` indica o início da palavra.
- `[01]*` permite zero ou mais símbolos `0` ou `1` antes do final.
- `00` obriga a palavra a terminar com dois zeros.
- `$` indica o fim da palavra.

### Exemplos aceitos

| Palavra | Resultado | Motivo |
|---|---|---|
| `00` | Aceita | Termina em `00` |
| `100` | Aceita | Termina em `00` |
| `0100` | Aceita | Termina em `00` |
| `11100` | Aceita | Termina em `00` |
| `0000` | Aceita | Termina em `00` |

### Exemplos rejeitados

| Palavra | Resultado | Motivo |
|---|---|---|
| `ε` | Rejeitada | Palavra vazia |
| `0` | Rejeitada | Não possui dois zeros finais |
| `01` | Rejeitada | Termina em `01` |
| `101` | Rejeitada | Termina em `01` |
| `001` | Rejeitada | Termina em `01` |

---

## 2. Palavras sobre `{a,b}` com exatamente dois `a`

### Linguagem

Considere:

```text
Σ = {a,b}
```

A linguagem contém todas as palavras que possuem exatamente duas ocorrências do símbolo `a`.

Formalmente:

```text
L = { w ∈ {a,b}* | w possui exatamente dois símbolos a }
```

### Expressão regular

```regex
^b*ab*ab*$
```

### Justificativa

A expressão pode ser dividida da seguinte forma:

```text
b* a b* a b*
```

- `b*` permite qualquer quantidade de `b` antes do primeiro `a`.
- O primeiro `a` é obrigatório.
- Outro `b*` permite qualquer quantidade de `b` entre os dois `a`.
- O segundo `a` é obrigatório.
- O último `b*` permite qualquer quantidade de `b` depois do segundo `a`.

Como existem somente dois `a` escritos explicitamente na Regex, nenhuma palavra com três ou mais `a` é aceita.

### Exemplos aceitos

| Palavra | Resultado | Quantidade de `a` |
|---|---|---:|
| `aa` | Aceita | 2 |
| `aba` | Aceita | 2 |
| `aabb` | Aceita | 2 |
| `baabbb` | Aceita | 2 |
| `bbabbab` | Aceita | 2 |

### Exemplos rejeitados

| Palavra | Resultado | Motivo |
|---|---|---|
| `ε` | Rejeitada | Possui 0 `a` |
| `bbb` | Rejeitada | Possui 0 `a` |
| `a` | Rejeitada | Possui apenas 1 `a` |
| `aaa` | Rejeitada | Possui 3 `a` |
| `bababa` | Rejeitada | Possui 3 `a` |

---

## 3. Identificador com duas maiúsculas, três algarismos e uma minúscula opcional

### Regra

O identificador deve possuir:

1. exatamente duas letras maiúsculas;
2. exatamente três algarismos;
3. opcionalmente, uma única letra minúscula no final.

### Linguagem

```text
L = { identificadores formados por 2 letras maiúsculas,
      seguidas de 3 algarismos,
      seguidos opcionalmente por 1 letra minúscula }
```

### Expressão regular

```regex
^[A-Z]{2}[0-9]{3}[a-z]?$
```

### Justificativa

- `^` marca o início.
- `[A-Z]{2}` exige exatamente duas letras maiúsculas.
- `[0-9]{3}` exige exatamente três algarismos.
- `[a-z]?` permite zero ou uma letra minúscula.
- `$` marca o fim e impede caracteres extras.

### Exemplos aceitos

| Identificador | Resultado |
|---|---|
| `AB123` | Aceito |
| `ZX007` | Aceito |
| `RT999a` | Aceito |
| `CC202z` | Aceito |
| `XY000m` | Aceito |

### Exemplos rejeitados

| Identificador | Resultado | Motivo |
|---|---|---|
| `A123` | Rejeitado | Apenas uma maiúscula |
| `ABC123` | Rejeitado | Três maiúsculas |
| `AB12` | Rejeitado | Apenas dois algarismos |
| `AB123xy` | Rejeitado | Duas minúsculas no final |
| `ab123` | Rejeitado | Letras iniciais não são maiúsculas |
| `AB123M` | Rejeitado | O caractere opcional deve ser minúsculo |
| `AB-123` | Rejeitado | Hífen não faz parte do formato |

---

# Desafio — Matrícula acadêmica

## Formato exigido

```text
CURSO-ANO-NÚMERO-TURNO
```

Regras:

- `CURSO`: `CCO`, `ESW` ou `SIS`;
- `ANO`: de `2024` até `2029`;
- `NÚMERO`: exatamente quatro algarismos;
- `TURNO`: `M`, `T` ou `N`;
- os blocos devem ser separados por hífen;
- não devem existir caracteres antes ou depois da matrícula.

## Expressão regular

```regex
^(CCO|ESW|SIS)-202[4-9]-[0-9]{4}-[MTN]$
```

Uma versão equivalente usando grupo não capturante é:

```regex
^(?:CCO|ESW|SIS)-202[4-9]-[0-9]{4}-[MTN]$
```

## Justificativa de cada bloco

### 1. Início da entrada

```regex
^
```

Garante que a correspondência começa no primeiro caractere da entrada.

### 2. Curso

```regex
(CCO|ESW|SIS)
```

Aceita somente uma das três opções:

```text
CCO
ESW
SIS
```

O operador `|` significa "ou".

### 3. Primeiro hífen

```regex
-
```

Obriga a existência do hífen entre curso e ano.

### 4. Ano

```regex
202[4-9]
```

- `202` é fixo;
- `[4-9]` permite os algarismos de 4 até 9.

Portanto, os anos possíveis são:

```text
2024
2025
2026
2027
2028
2029
```

### 5. Segundo hífen

```regex
-
```

Separa o ano do número acadêmico.

### 6. Número

```regex
[0-9]{4}
```

Exige exatamente quatro algarismos.

Exemplos:

```text
0000
0001
1234
9999
```

### 7. Terceiro hífen

```regex
-
```

Separa o número do turno.

### 8. Turno

```regex
[MTN]
```

Aceita apenas:

- `M` — manhã;
- `T` — tarde;
- `N` — noite.

### 9. Fim da entrada

```regex
$
```

Garante que nenhum caractere extra seja permitido após o turno.

---

# Tabela de testes — Matrícula acadêmica

## Casos válidos

| Entrada | Esperado | Justificativa |
|---|---|---|
| `CCO-2024-0000-M` | Aceita | Menor ano permitido e quatro dígitos |
| `CCO-2029-9999-N` | Aceita | Maior ano permitido |
| `ESW-2026-1234-T` | Aceita | Todos os blocos estão corretos |
| `SIS-2025-0001-M` | Aceita | Número com zeros à esquerda é permitido |
| `SIS-2028-9876-N` | Aceita | Formato completo válido |

## Casos inválidos

| Entrada | Esperado | Regra violada |
|---|---|---|
| `ADS-2026-1234-M` | Rejeita | Curso não permitido |
| `CCO-2023-1234-M` | Rejeita | Ano abaixo do limite |
| `CCO-2030-1234-M` | Rejeita | Ano acima do limite |
| `CCO-2026-123-M` | Rejeita | Número possui apenas 3 dígitos |
| `CCO-2026-12345-M` | Rejeita | Número possui 5 dígitos |
| `CCO-2026-12A4-M` | Rejeita | Número contém letra |
| `CCO-2026-1234-X` | Rejeita | Turno inválido |
| `CCO2026-1234-M` | Rejeita | Falta o primeiro hífen |
| `CCO-2026-1234M` | Rejeita | Falta o último hífen |
| `CCO_2026_1234_M` | Rejeita | Separador incorreto |
| `cco-2026-1234-M` | Rejeita | Curso em letras minúsculas |
| `CCO-2026-1234-m` | Rejeita | Turno em minúscula |
| `XCCO-2026-1234-M` | Rejeita | Caractere extra no início |
| `CCO-2026-1234-MX` | Rejeita | Caractere extra no final |
| ` CCO-2026-1234-M` | Rejeita | Espaço extra no início |
| `CCO-2026-1234-M ` | Rejeita | Espaço extra no final |

---

# Casos de fronteira

Os casos de fronteira verificam os limites exatos das regras.

| Teste | Resultado | Explicação |
|---|---|---|
| `CCO-2024-0000-M` | Aceita | Menor ano permitido |
| `CCO-2029-9999-N` | Aceita | Maior ano permitido |
| `CCO-2023-0000-M` | Rejeita | Um ano abaixo do mínimo |
| `CCO-2030-9999-N` | Rejeita | Um ano acima do máximo |
| `ESW-2026-0000-T` | Aceita | Menor número possível com 4 dígitos |
| `ESW-2026-9999-T` | Aceita | Maior número possível com 4 dígitos |
| `ESW-2026-999-T` | Rejeita | Apenas 3 algarismos |
| `ESW-2026-10000-T` | Rejeita | 5 algarismos |

---

# Entradas quase corretas

São entradas próximas do formato correto, úteis para encontrar erros na Regex.

| Entrada | Resultado esperado | Problema |
|---|---|---|
| `CCO-2026-1234-M` | Aceita | Entrada totalmente correta |
| `CC0-2026-1234-M` | Rejeita | Foi usado zero no lugar de `O` |
| `CCO-2026-1234-m` | Rejeita | Turno em minúscula |
| `CCO-2026-123-M` | Rejeita | Falta um algarismo |
| `CCO-2026-01234-M` | Rejeita | Há um algarismo a mais |
| `CCO-2026-1234-MM` | Rejeita | Dois caracteres de turno |
| `CCO--2026-1234-M` | Rejeita | Hífen extra |
| `CCO-2026--1234-M` | Rejeita | Hífen extra |
| `CCO-2026-1234-` | Rejeita | Turno ausente |

---

# Como identificar uma regra mal representada quando um teste falha

Se uma entrada inválida estiver sendo aceita, deve-se verificar qual parte da Regex está permissiva demais.

Exemplos:

### Problema: aceita qualquer curso

Regex incorreta:

```regex
^[A-Z]{3}-202[4-9]-[0-9]{4}-[MTN]$
```

Essa Regex aceitaria `ADS`, `ABC`, `XYZ` etc.

Correção:

```regex
^(CCO|ESW|SIS)-202[4-9]-[0-9]{4}-[MTN]$
```

### Problema: aceita anos fora do intervalo

Regex incorreta:

```regex
^...-[0-9]{4}-...$
```

Ela aceitaria qualquer ano com quatro algarismos.

Correção:

```regex
202[4-9]
```

### Problema: aceita quantidade errada de algarismos

Regex incorreta:

```regex
[0-9]+
```

O `+` significa "um ou mais", portanto não limita a quatro dígitos.

Correção:

```regex
[0-9]{4}
```

### Problema: aceita caracteres extras

Regex incorreta:

```regex
(CCO|ESW|SIS)-202[4-9]-[0-9]{4}-[MTN]
```

Sem `^` e `$`, alguns motores podem encontrar essa sequência dentro de uma string maior.

Correção:

```regex
^(CCO|ESW|SIS)-202[4-9]-[0-9]{4}-[MTN]$
```

---

# Questões para reflexão

## 1. Toda expressão regular formal representa uma linguagem regular?

**Sim.**

Por definição, uma expressão regular formal é construída utilizando operações que preservam a regularidade, como:

- união;
- concatenação;
- fecho de Kleene (`*`).

Assim, toda expressão regular formal descreve uma linguagem regular.

---

## 2. Toda linguagem regular possui uma expressão regular?

**Sim.**

O Teorema de Kleene estabelece a equivalência entre:

```text
Expressões Regulares
        ⇕
Autômatos Finitos
```

Portanto, se uma linguagem é reconhecida por um autômato finito, existe uma expressão regular que representa essa mesma linguagem.

---

## 3. Como uma Regex se relaciona com DFA e NFA?

Expressões regulares, DFA e NFA possuem o mesmo poder de reconhecimento quando estamos falando da teoria clássica das linguagens regulares.

As equivalências são:

```text
Regex ⇔ NFA ⇔ DFA
```

É possível:

1. converter uma Regex em um NFA;
2. converter um NFA em um DFA;
3. converter um DFA em uma Regex.

Eles podem ter estruturas diferentes, mas reconhecem exatamente a mesma classe de linguagens: **as linguagens regulares**.

### DFA

DFA significa:

```text
Deterministic Finite Automaton
```

Em cada estado e para cada símbolo do alfabeto existe exatamente uma transição possível.

### NFA

NFA significa:

```text
Nondeterministic Finite Automaton
```

Pode existir mais de uma transição possível para o mesmo símbolo e, dependendo da definição utilizada, também podem existir transições `ε`.

Mesmo sendo mais flexível na representação, um NFA não possui mais poder de reconhecimento que um DFA.

---

## 4. Quais extensões de motores de Regex não pertencem à definição clássica?

As Regex usadas em linguagens de programação normalmente oferecem recursos que não fazem parte da definição matemática clássica de expressão regular.

Alguns exemplos são:

- **backreferences**, como `\1`;
- **lookahead**, como `(?=...)`;
- **negative lookahead**, como `(?!...)`;
- **lookbehind**, como `(?<=...)`;
- **negative lookbehind**, como `(?<!...)`;
- **grupos condicionais**;
- **grupos atômicos**;
- **recursão**, disponível em alguns motores.

É importante observar que "Regex de programação" e "expressão regular formal" não são necessariamente a mesma coisa.

Alguns desses recursos são apenas extensões de sintaxe, enquanto outros, especialmente **backreferences** e mecanismos de **recursão**, podem permitir reconhecer padrões que vão além das linguagens regulares.

---

## 5. Por que `{aⁿbⁿ | n ≥ 0}` não pode ser reconhecida por um DFA?

A linguagem é:

```text
L = { aⁿbⁿ | n ≥ 0 }
```

Alguns exemplos pertencentes à linguagem são:

```text
ε
ab
aabb
aaabbb
aaaabbbb
```

Para aceitar uma palavra, o autômato teria que verificar se:

1. todos os `a` aparecem primeiro;
2. depois aparecem os `b`;
3. a quantidade de `b` é exatamente igual à quantidade de `a`.

O problema é que um DFA possui uma quantidade **finita de estados**.

Para reconhecer essa linguagem, ele precisaria "lembrar" quantos `a` foram lidos, para depois conferir a mesma quantidade de `b`.

Como `n` pode crescer sem limite, seria necessário armazenar uma quantidade arbitrariamente grande de informação.

Um DFA não possui memória ilimitada.

Por isso:

```text
{aⁿbⁿ | n ≥ 0}
```

**não é uma linguagem regular** e, consequentemente, não pode ser reconhecida por um DFA.

Esse resultado também pode ser demonstrado formalmente pelo **Lema do Bombeamento para Linguagens Regulares** ou pelo **Teorema de Myhill-Nerode**.

---

# Resumo das principais Regex

| Exercício | Regex |
|---|---|
| Binárias que terminam em `00` | `^[01]*00$` |
| Exatamente dois `a` sobre `{a,b}` | `^b*ab*ab*$` |
| 2 maiúsculas + 3 algarismos + minúscula opcional | `^[A-Z]{2}[0-9]{3}[a-z]?$` |
| Matrícula acadêmica | `^(CCO\|ESW\|SIS)-202[4-9]-[0-9]{4}-[MTN]$` |

> Observação: na tabela acima, as barras `\` antes de `|` servem apenas para exibir corretamente o caractere dentro da tabela Markdown. A Regex para matrícula deve ser escrita como:
>
> ```regex
> ^(CCO|ESW|SIS)-202[4-9]-[0-9]{4}-[MTN]$
> ```

---

# Conclusão

As expressões regulares construídas atendem às restrições propostas e os casos de teste verificam tanto entradas válidas quanto inválidas, incluindo situações de fronteira e entradas quase corretas.

Para o desafio da matrícula acadêmica, a expressão final recomendada é:

```regex
^(CCO|ESW|SIS)-202[4-9]-[0-9]{4}-[MTN]$
```

Ela garante simultaneamente o curso permitido, o intervalo correto de anos, exatamente quatro algarismos no número, um turno válido, os hífens obrigatórios e a ausência de caracteres extras.
