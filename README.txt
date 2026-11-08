Copia esses 2 arquivos para dentro da pasta payloads logo carregas o payload pelo gold hen


DualSenseBT — touchpad, giroscópio e autocentramento experimental

BIN: DualSenseBT.bin
Alvo: payload existente para PS4 GoldHEN 12.00.

Esta versão foi compilada e passou testes sintéticos locais. Não foi executada
na consola, nem há confirmação de funcionamento do movimento nos jogos.
O BIN original da pasta do utilizador não foi substituído.

FUNCIONALIDADES EXISTENTES PRESERVADAS
- Ligação DualSense por Bluetooth e entrada virtual para a PS4.
- Botões, direcionais, analógicos, L2/R2 e botão PS.
- Rotina de touchpad com dois contactos e clique independente.
- Cores RGB e efeitos de luz fixa, pulsação e alternância de cores.
- Cinco modos de gatilho: desligado, resistência, arma, vibração fixa e
  resposta à vibração do jogo. O último depende de o jogo fornecer rumble;
  não corresponde a efeitos adaptativos nativos de jogos PS5.
- Força, início e frequência dos efeitos ajustáveis.
- Indicador aproximado de bateria em quatro LEDs brancos exteriores.
- Consulta da bateria, estado de carga e avisos configuráveis.
- Painel AltSense e gravação das definições.

ATALHOS — CONFIGURAÇÃO ATUAL: CREATE
Manter Create e premir:
- L1: mudar de cor.
- R1: mudar o modo dos gatilhos.
- Cima: consultar bateria.
- L2: diminuir força dos gatilhos em 16, até ao mínimo 0.
- R2: aumentar força dos gatilhos em 16, até ao máximo 128.
- Options: abrir/fechar painel AltSense.

PAINEL ALTSENSE
- Cima/Baixo: selecionar opção.
- Esquerda/Direita: alterar opção.
- X: avançar/alternar o valor da opção selecionada.
- O: fechar.
Opções: cor, efeito de luz, modo dos gatilhos, força, indicador de bateria
nos LEDs e consulta da bateria. O painel neutraliza os botões/analógicos
enviados ao jogo enquanto está aberto.

CORES DOS ATALHOS
Azul, vermelho, verde, roxo, laranja, branco e apagado.
RGB personalizado também pode ser definido no ficheiro de configuração.
O efeito de alternância de cores percorre seis cores.

CONFIGURAÇÃO
Ficheiro existente na PS4: /data/payloads/DualSenseBT_config.txt
shortcut_button=1 usa Create; shortcut_button=0 usa PS como modificador.
O ficheiro é relido aproximadamente a cada dois segundos.
Esta entrega não substitui o ficheiro de configuração existente.

BATERIA — ESTIMATIVA
4 LEDs: mais de 75%; 3 LEDs: mais de 50% até 75%;
2 LEDs: mais de 25% até 50%; 1 LED: mais de 0% até 25%.
O LED central fica apagado. A leitura do comando é aproximada, não uma
medição exata em passos de 1%. Aviso de bateria baixa: 15% ou menos,
quando os avisos estão ativados.

NOVAS FUNÇÕES — IMPLEMENTADAS, AINDA EXPERIMENTAIS
- Descodificação de giroscópio e acelerómetro nos relatórios Bluetooth completos.
- Velocidade angular e aceleração enviadas na estrutura de entrada da PS4.
- Orientação relativa calculada por integração do giroscópio e normalizada.
- Calibração automática do desvio do giroscópio após cerca de dois segundos
  de amostras aceites como repouso; reinicia a orientação relativa nessa altura.
- Correção automática do centro dos quatro eixos dos analógicos após cerca
  de dois segundos de estabilidade junto ao centro.
- Zona morta de três unidades após correção, preservando os extremos 0 e 255.
- Centros aprendidos ficam fixos durante a sessão, para evitar seguir um
  analógico mantido inclinado. Não são guardados permanentemente no comando.

PARA CALIBRAR
Depois de ligar, colocar o comando numa superfície estável, soltar ambos os
analógicos e aguardar pelo menos três segundos. Movimento ou instabilidade
podem adiar a calibração. Ainda não há aviso visual específico de conclusão.
Estas funções são automáticas e não acrescentam atalhos.

LIMITAÇÕES DAS NOVAS FUNÇÕES
- Usa escalas nominais dos sensores; ainda não lê calibração de fábrica 0x05.
- A orientação é relativa: não existe referência absoluta de direção nem fusão
  completa com o acelerómetro para compensar deriva de orientação.
- Compatibilidade e sentido dos eixos nos jogos precisam de validação real.
- Analógicos demasiado afastados do centro não são recalibrados; não corrige
  desgaste físico grave. Uma posição intencional ligeiramente inclinada e
  mantida estável durante a calibração pode ser confundida com o centro.
- Relatórios simples não contêm os dados necessários de movimento/touchpad.
- Pausas longas nos dados reiniciam o estado de calibração.

AINDA NÃO IMPLEMENTADO
- Áudio do altifalante do comando.
- Áudio na saída de auscultadores e integração das rotas de áudio da PS4.
- Microfone interno ou do auricular, incluindo integração no chat.
- Emparelhamento Bluetooth automático através do cabo USB na PS4.
- Calibração de fábrica dos sensores, ajuste térmico contínuo e fusão completa.
- Atalhos ou opções de painel para ativar/desativar/configurar as novas calibrações.

VALIDAÇÃO DESTA ENTREGA
Testes locais com deteção de acessos inválidos e comportamento indefinido:
calibração, centro, extremos, rotação, normalização da orientação, preservação
dos outros campos, relatório simples e rollover/pausas do relógio do sensor.
O único desvio alterado dentro do BIN de referência está em 0xA3A0;
o novo código e o seu estado foram acrescentados ao fim. As rotinas antigas
de LEDs/gatilhos/bateria permaneceram byte a byte iguais.
Não executar simultaneamente duas instâncias da ponte.
