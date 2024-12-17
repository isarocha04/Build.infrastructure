
# Projeto Terraform - Provisionamento de EC2 na AWS

## Passo a Passo

### **Pré-requisitos**

- Instalar o **Terraform CLI**
- Instalar o **AWS CLI**
- Configurar suas credenciais AWS:

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
📸 **Print:**Resultado do comando `terraform init`.



#### **Formatar o código**
```bash
terraform fmt
terraform validate
```
📸 **Print:**Resultado da validação com `terraform validate`.

---

### **Aplicando a Configuração**

#### **Criar a Infraestrutura**
```bash
terraform apply
```
Digite `yes` para confirmar a criação dos recursos.

📸 **Print:**Resultado do comando `terraform apply` mostrando os recursos provisionados.

---

### **Verificando Recursos**

#### **Console AWS**
- Acessar o console AWS EC2 e verificar a instância criada.
- Tag: **ExampleAppServerInstance**
📸 **Print:** Console AWS exibindo a instância provisionada.

---

### **Documentação dos Recursos Provisionados**

- **Instância EC2**
  - Nome: `ExampleAppServerInstance`
  - Tipo: `t2.micro`
  - AMI: `ami-830c94e3`
  - Região: `us-west-2`

---

### **Destruindo a Infraestrutura**

Se necessário, remova os recursos provisionados:

```bash
terraform destroy
```
Digite `yes` para confirmar.

📸 **Print:** Resultado do `terraform destroy`.

---

## Estrutura Final do Projeto

```bash
terraform-aws-setup/
│-- main.tf
│-- .terraform/    # Gerado após o terraform init
│-- terraform.tfstate
```

---

## Conclusão
Este projeto demonstrou como provisionar uma instância EC2 na AWS utilizando Terraform como **Infraestrutura como Código (IaC)**.
