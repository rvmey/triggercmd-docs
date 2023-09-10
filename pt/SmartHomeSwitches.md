# Interruptores Virtuais para Casa Inteligente

## Integrações que criam interruptores virtuais

* Habilidade Alexa TRIGGERcmd Smart Home
* Ação Google Assistant TRIGGERcmd Smart Home
* Integração TRIGGERcmd Samsung SmartThings

## Criação e nomeação dos interruptores

Tanto os comandos quanto os computadores têm um campo de **voz** que determina como seus interruptores virtuais serão nomeados. Se esses campos de voz estiverem vazios, um interruptor virtual pode não ser criado. 

Para que um interruptor virtual seja criado, cada um dos seus comandos deve ter um valor no campo de **voz** (como "calculadora"), porque o valor do campo de **voz** do comando é usado no nome do interruptor virtual.

Para que um interruptor virtual seja criado, cada um dos seus computadores também deve ter um valor no campo de **voz** (como "laptop"), porque o valor do campo de **voz** do computador é usado no nome do interruptor virtual (exemplo: **calculadora no laptop**). 

A exceção é o seu computador padrão. O campo de voz do seu computador padrão pode estar vazio porque não é usado nos nomes dos seus interruptores virtuais. Em vez disso, apenas os valores dos campos de voz dos comandos são usados (exemplo: **calculadora**).

O primeiro computador na sua conta é o seu computador padrão por padrão, mas se você tiver vários computadores, pode alterar o seu computador padrão. 

Interruptores virtuais para o seu computador padrão são:

1. Nomeados apenas com o valor do campo de voz do comando (ou seja, calculadora).
1. Criados se o campo de voz do computador estiver vazio ou não.

Interruptores virtuais para os seus computadores não padrão são:

1. Nomeados com os valores dos campos de voz do comando e do computador (ou seja, calculadora no laptop).
1. Serão criados mesmo que o campo de voz do seu computador padrão esteja vazio.

# Ligando e Desligando Interruptores Virtuais

Se o seu comando tiver "Permitir Parâmetros" definido como verdadeiro e o campo "Comando de Desativação" estiver vazio, quando você liga ou desliga o interruptor virtual do comando, ele executará o seu comando com **on** ou **off** como parâmetro do comando.

Ou, se você colocar um comando no campo "Comando de Desativação", ele será executado quando você desligar o interruptor.

Se "Permitir Parâmetros" estiver definido como falso, o comando no campo "Comando" será executado, quer você ligue ou desligue o interruptor.