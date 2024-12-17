
# Terraform 

## Passo a Passo

### **Pré-requisitos**

- Instalar  **Terraform CLI**
- Instalar  **AWS CLI**
- Configurar credenciais AWS

```bash
export AWS_ACCESS_KEY_ID=SEU_ACCESS_KEY
export AWS_SECRET_ACCESS_KEY=SEU_SECRET_KEY
```

### **Estrutura do Projeto**
Criar um diretório e o arquivo de configuração principal
```bash
mkdir terraform-aws-setup
cd terraform-aws-setup
touch main.tf
```

### **Arquivo `main.tf`**
Adicione a configuração abaixo para provisionar uma instância EC2

```hcl
terraform {
  required_providers {
    aws = {
      source  = "hashicorp/aws"
      version = "~> 4.16"
    }
  }
  required_version = ">= 1.2.0"
}

provider "aws" {
  region = "us-west-2"
}

resource "aws_instance" "app_server" {
  ami           = "ami-830c94e3" # Ubuntu AMI (us-west-2)
  instance_type = "t2.micro"

  tags = {
    Name = "ExampleAppServerInstance"
  }
}
```

---

### **Inicialização e Validação**

#### **Inicializar o Terraform**
```bash
terraform init
```
![image](https://github.com/user-attachments/assets/a835edae-3c2b-491c-b553-0133aceb85cd)

---

### **Aplicando a Configuração**

#### **Criar a Infraestrutura**
```bash
terraform apply
```
Digite `yes` para confirmar a criação dos recursos.

<img width="566" alt="Captura de Tela 2024-12-17 às 11 10 22" src="https://github.com/user-attachments/assets/9c82afd5-e120-4748-921f-73ff8c16afc0" />

---

### **Verificando Recursos**

#### **Console AWS**
- Acessar o console AWS EC2 e verificar a instância criada.
- Tag: **ExampleAppServerInstance**


<img width="1678" alt="Captura de Tela 2024-12-17 às 11 18 44" src="https://github.com/user-attachments/assets/1bcdc8f1-8bfb-4a10-a1e4-1993653e844c" />



---

- **Instância EC2**
  - Nome: `ExampleAppServerInstance`
  - Tipo: `t2.micro`
  - AMI: `ami-830c94e3`
  - Região: `us-west-2`

---

## Estrutura Final do Projeto

```bash
terraform-aws-setup/
│-- main.tf
│-- .terraform/    # Gerado após o terraform init
│-- terraform.tfstate
```

---

