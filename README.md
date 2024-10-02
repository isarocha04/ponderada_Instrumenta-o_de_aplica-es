# OpenTelemetry Go Application Monitoring

  Aqui temosa implementação do exemplo que encontramos no artigo “Complete guide to implementing OpenTelemetry in Go applications”. Nele, temos as etapas para configurar o SDK do OpenTelemetry, organizar uma aplicação Go, e integrar com a ferramenta SigNoz para realizarmos 
  o monitoramento e visualizarmos as métricas.

## Requisitos
- Go 1.18 ou superior instalado
- Docker Engine
- Git instalado

## Instalação
### 1. Clonar o repositório

```bash
git clone https://github.com/SeuUsuario/open-telemetry-go-example.git
cd open-telemetry-go-example
```

### 2. Instalar dependências do Go

```bash
go mod tidy
```

### 3. Instalar e configurar o SigNoz

Instale o SigNoz utilizando o seguinte script:
```bash
git clone -b main https://github.com/SigNoz/signoz.git
cd signoz/deploy/
./install.sh
```
Acessar SigNoz em : `http://localhost:3301/application` após a instalação.

### 4. Configurar variáveis de ambiente

Defina as variáveis de ambiente para configurar o OpenTelemetry:
```bash
export SERVICE_NAME="goGinApp"
export OTEL_EXPORTER_OTLP_ENDPOINT="localhost:4317"
export INSECURE_MODE=true
```

## Exemplos

```bash
go run main.go
```

### Gerando dados de monitoramento

Utilizar o endpoint `/books` para gerar dados de telemetria
```bash
curl http://localhost:8090/books
```

Repitir algumas vezes e acessar o dashboard do SigNoz para visualizar os dados.


## Técnicas e Conceitos de TDD

Nesse projeto se encaixam conceitos de TDD para garantir a funcionalidade correta durante o desenvolvimento. 

1. **Criação de Testes Unitários**: Utilizamos o pacote `testing`  do Go para desenvolver testes unitários antes de implementar funcionalidades. Isso garante que o código esteja sendo escrito para passar em testes já definidos.
2. **Cobertura de Código**: A cobertura de código foi aumentada progressivamente à medida que novos testes foram adicionados, garantindo que o comportamento da aplicação seja validado de forma abrangente.
3. **Testes de Integração**: O OpenTelemetry foi integrado ao sistema, e testes de integração foram escritos para verificar se as métricas estão sendo  exportadas para o SigNoz. Estes testes garantem que todos os processos estejam funcionando corretamente.

## Conclusão 

Nesse exemplo integramos o OpenTelemetry em uma aplicação Go, facilitando o monitoramento a partir SigNoz. Usamos também técnicas de TDD para garantir que o código esteja funcionando bem e seja fácil de manter. A documentação e os comentários no código ajudam a entendermos cada passo, tornando o processo mais simples e direto para quem for trabalhar no projeto.


