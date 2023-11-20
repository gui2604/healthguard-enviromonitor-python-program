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
  <img src="https://github.com/gui2604/healthguard-enviromonitor-python-program/assets/128194162/caee3f66-d1e2-42d3-9aa6-118fd428a042" width=700px>
</div>

<p>Por meio dessa tela será possível o profissional da saúde acompanhar todos os dados medidos em cada cômodo, relacionado ao respectivo paciente e sua ficha, também podendo consultar cada paciente seu cadastrado.</p>
<h3>Sistema:</h3>
<p>Para isso, o sistema do funcionamento desse software foi escrito em Python, e o código fonte constitui-se da seguinte forma:</p>

<div align="center">
  <img src="https://github.com/gui2604/healthguard-enviromonitor-python-program/assets/128194162/9ffabbc4-d135-4066-a515-726f0c2eff24" width="700px">
</div>

- Um “import json” com a finalidade de consumir e gerar arquivos externos, que serão os dados oriundos do sistema arduíno coletado pelos sensores instalados nos cômodos de cada paciente. 
- Uma função “forca_opcao” para forçar a opção do usuário digitar apenas as opções possíveis.
- Uma função “print_dic” para printar dicionários a fim de tornar os dados armazenados nos dicionários mais visíveis
- Uma função “fazer_login” de autenticação de login, pedindo usuário, senha e crm do médico **(para fins de teste adotar usuário=”usuario123”, senha=”senha123” e crm=”123”)** que usará o sistema para monitorar o ambiente de seus pacientes.

<div align="center">
  <img src="https://github.com/gui2604/healthguard-enviromonitor-python-program/assets/128194162/6401a83c-d514-4c79-8923-b574b698cfef" width="700px">
</div>

<p>Uma função de cadastro de paciente “cadastrar_paciente”, responsável por realizar o cadastro de um paciente no sistema. Ela cria um novo dicionário chamado “novo_paciente”, que é um dicionário que armazenará todos os dados do paciente. A função analisa qual é o tipo de dado que existe nos dicionários de pacientes já armazenados, a fim de guardar os dados corretamente, veja a lista de pacientes:</p>
<div align="center">
  <img src="https://github.com/gui2604/healthguard-enviromonitor-python-program/assets/128194162/e0e991bc-f32c-47ee-87ed-d905478c9bcc" width="700px">
</div>

<p>Essa é uma lista de pacientes, que guarda os dicionários de cadastro de cada paciente. Esse é um exemplo de um paciente. A função separa corretamente os inputs do usuário em cada tipo de dado presente na ficha do paciente, caso seja um dicionário, nesse caso o “cômodos” significa que um novo cômodo do paciente está prestes a ser cadastrado, e o programa irá consumir um arquivo externo para armazenar os dados coletados daquele cômodo, que virá no formato .json já especificado no próprio arquivo externo que o Arduino terá enviado, sendo adicionado no dicionário de cômodos do paciente.
No final da função de cadastro, esse dicionário “novo_paciente” será adicionado à lista de pacientes: “pacientes”, cadastrando-o no sistema.
A função “alterar_paciente” permite o usuário alterar dados de um paciente cadastrado, caso necessário:
</p>

<div align="center">
  <img src="https://github.com/gui2604/healthguard-enviromonitor-python-program/assets/128194162/3ff2bae3-3643-4148-8460-c997c6c9358b" width="700px">
</div>

<p>Ela primeiramente exibe, enumerando todos os pacientes cadastrados e pele para o usuário digitar o número correspondente do paciente cadastrado que deseja realizar alterações. Ela força o usuário a escolher apenas pacientes que estão cadastrados e pergunta qual dado específico o usuário deseja alterar. O programa avalia o tipo de dado escolhido e toma uma decisão de acordo com o tipo de dado, caso seja um dicionário, ele prevê que se trata dos cômodos e consome um arquivo externo para atualizar os cômodos desse paciente, caso contrário apenas pede para o usuário digitar o novo dado.
No final da função, ela pergunta se o usuário quer continuar alterando mais dados desse paciente, caso contrário, encerra a operação.
</p>

<div align="center">
  <img src="https://github.com/gui2604/healthguard-enviromonitor-python-program/assets/128194162/cf917d17-006c-4d19-b18e-200e49a87017" width="700px">
</div>

<p>A função “deletar_paciente” permite ao usuário deletar um paciente cadastrado. Ela enumera os pacientes cadastrados e pede para o usuário digitar o número correspondente atribuído na enumeração, forçando essa opção e posteriormente removendo todo o dicionário desse paciente da lista de pacientes.
A função “consultar_paciente” permite o usuário a consultar todos os dados do dicionário de um determinado paciente. Ele faz a enumeração dos pacientes e pede para o usuário digitar o número corresponde atribuído nessa enumeração, exibindo os dados do dicionário completo desse paciente utilizando a função “print_dic”.
Aqui está a execução do programa propriamente dito:
</p>

<div align="center">
  <img src="" width="700px">
</div>
