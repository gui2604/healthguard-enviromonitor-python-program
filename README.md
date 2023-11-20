<h1> Healthguard EnviroMonitor </h1>
<h3>1ESR</h3>
<h3>Guilherme Barreto Santos - RM97674</h3>
<h3>Nicolas Oliveira da Silva - RM98939</h3>

<h2>Proposta de Solução:</h2>
<p>A Organização Mundial da Saúde (OMS) estima que 12,6 milhões de óbitos ocorrem anualmente devido a condições ambientais precárias. Isso destaca a importância de abordar a saúde em ambientes domésticos e públicos, evidenciando que a negligência nessas condições pode agravar problemas de saúde. A aplicação inteligente da tecnologia para coletar dados relevantes é fundamental para a tomada de decisões na área da saúde, podendo prevenir o agravamento de doenças devido a condições insalubres em diversos contextos, como residências e locais de trabalho.
Nesse contexto, o projeto HealthGuard EnviroMonitor propõe um dispositivo equipado com um circuito Arduino, integrando sensores DHT11 (umidade e temperatura) e LDR (luminosidade). A placa ESP32 transmite em tempo real os dados coletados para o software HealthGuard EnviroMonitor, destinado a profissionais de saúde, como médicos, permitindo o monitoramento em tempo real do ambiente dos pacientes. A instalação do dispositivo em locais onde os pacientes permanecem por períodos prolongados, como residências e ambientes de trabalho, possibilita a coleta de dados e o envio via protocolo MQTT.
Diversos ambientes podem apresentar características não perceptíveis que afetam a saúde e muitas vezes são negligenciadas. Exemplos incluem a umidade, onde a recomendação da OMS é entre 50% e 60%, pois índices superiores favorecem a proliferação de fungos e bactérias. A baixa umidade, por outro lado, pode causar problemas respiratórios. A luminosidade inadequada pode contribuir para a proliferação de microrganismos, enquanto a exposição excessiva à luz intensa pode ter efeitos prejudiciais à saúde.
Similarmente, a medição da temperatura média do ambiente é crucial para a salubridade, especialmente em profissões que envolvem exposição prolongada a condições extremas. Esses três elementos – umidade, luminosidade e temperatura – constituem a base do projeto HealthGuard EnviroMonitor. 
</p>
<div align="center">
  <img src="https://github.com/gui2604/healthguard-enviromonitor-python-program/assets/128194162/314fc0f3-e2c1-4d5e-9955-6603b2946760" width=700px>
</div>
<p>O monitoramento desses fatores em ambientes residenciais e profissionais permite análises em tempo real pelos médicos, que podem oferecer recomendações personalizadas para melhorar as condições do ambiente e preservar a saúde dos pacientes, evitando complicações que poderiam ser negligenciadas sem monitoramento adequado.
Essa é a tela do software que o profissional de saúde terá acesso para monitorar as condições de salubridade do ambiente em que seus pacientes estão:
</p>
<div align="center">
  <img src="https://github.com/gui2604/healthguard-enviromonitor-python-program/assets/128194162/caee3f66-d1e2-42d3-9aa6-118fd428a042" width=700px align="center">
</div>
<p>Por meio dessa tela será possível o profissional da saúde acompanhar todos os dados medidos em cada cômodo, relacionado ao respectivo paciente e sua ficha, também podendo consultar cada paciente seu cadastrado.</p>
<h3>Sistema:</h3>
<p>Para isso, o sistema do funcionamento desse software foi escrito em Python, e o código fonte constitui-se da seguinte forma:</p>
<div align="center">
  <img src="https://github.com/gui2604/healthguard-enviromonitor-python-program/assets/128194162/9ffabbc4-d135-4066-a515-726f0c2eff24" width="700px">
</div>
Um “import json” com a finalidade de consumir e gerar arquivos externos, que serão os dados oriundos do sistema arduíno coletado pelos sensores instalados nos cômodos de cada paciente. 
Uma função *“forca_opcao”* para forçar a opção do usuário digitar apenas as opções possíveis.
Uma função *“print_dic”* para printar dicionários a fim de tornar os dados armazenados nos dicionários mais visíveis
Uma função *“fazer_login”* de autenticação de login, pedindo usuário, senha e crm do médico **(para fins de teste adotar usuário=”usuario123”, senha=”senha123” e crm=”123”)** que usará o sistema para monitorar o ambiente de seus pacientes.

