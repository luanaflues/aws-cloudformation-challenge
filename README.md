# Desafio AWS CloudFormation - Automação de Infraestrutura

## Introdução
Este repositório documenta minha implementação do desafio da DIO para criar uma infraestrutura automatizada com AWS CloudFormation. O projeto provisiona um bucket S3 e uma instância EC2 usando um template YAML, aplicando conceitos de infraestrutura como código (IaC).

## Pré-requisitos
- Conta AWS ativa (Free Tier recomendado)
- AWS CLI configurada (opcional)
- Git e GitHub configurados
- Editor de texto (ex.: VS Code)
- Key Pair para acesso SSH à instância EC2

## Passos Realizados
1. **Criação do Template**:
   - Criei um template YAML (`templates/infra-template.yaml`) para provisionar:
     - Um bucket S3 com nome único (`luanaflues-bucket-us-east-2-<conta>`).
     - Uma instância EC2 (t2.micro) com Amazon Linux 2023.
   - Usei parâmetros para tornar o template reutilizável.
2. **Validação e Implantação**:
   - Inicialmente, enfrentei um erro devido a um `ImageId` inválido (`ami-0e86e20dae9224db8`) para a região `us-east-2`.
   - Corrigi o `ImageId` para `ami-000a6b7d4a67ff033` (Amazon Linux 2023 em us-east-2) e validei o template.
   - Criei um stack chamado `LuanaInfraStack` na região `us-east-2`.
3. **Verificação**:
   - Confirmei a criação do bucket S3 e da instância EC2.
   - Capturei evidências visuais (veja a pasta `/images`).
4. **Documentação**:
   - Estruturei este README com detalhes do processo, incluindo a correção do erro.
   - Adicionei capturas de tela e o template no repositório.

## Resultados
- **Bucket S3**: Criado com sucesso. Nome gerado: `luanaflues-bucket-us-east-2-<conta>`.
- **Instância EC2**: Provisionada e rodando com IP público acessível.
- Capturas de tela:
  - [Stack no CloudFormation](images/captura1.png)
  - [Bucket S3](images/captura2.png)
  - [Instância EC2](images/captura3.png)

## Insights e Lições Aprendidas
- Aprendi a estruturar templates CloudFormation com parâmetros e saídas para maior flexibilidade.
- Entendi a importância de validar templates antes da implantação para evitar erros.
- Notei que nomes de buckets S3 devem ser globalmente únicos, exigindo cuidado na nomenclatura.
- Descobri que AMIs são específicas por região, e o `ImageId` deve corresponder à região do stack (ex.: `ami-000a6b7d4a67ff033` para us-east-2).
- O uso de tags facilita a organização e rastreamento de recursos na AWS.

## Referências
- [Documentação AWS CloudFormation](https://docs.aws.amazon.com/cloudformation/)
- [Guia de Markdown do GitHub](https://docs.github.com/en/get-started/writing-on-github)
- [AWS Samples - CloudFormation](https://github.com/awslabs/aws-cloudformation-templates)