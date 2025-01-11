# Отчёт по заданию Terraform

![./terraform --version.png](https://github.com/V3l337/ter-homeworks_01/blob/main/terraform%20--version.png)

## Задание 2

### В каком terraform-файле, согласно .gitignore, допустимо сохранить личную, секретную информацию?
Согласно файлу `.gitignore`, личную информацию (логины, пароли, ключи, токены и т.д.) допустимо сохранять в файле:

```plaintext
personal.auto.tfvars
```

---

## Задание 3

### Найденное секретное содержимое ресурса random_password:

Ключ:
```plaintext
"result"
```
Значение:
```plaintext
"IBsQN5FT0fzcczOq"
```

---

## Задание 4

### Ошибки при выполнении команды `terraform validate` после раскомментирования кода:

1. **Ошибка:**
```plaintext
Error: Missing name for resource
  on main.tf line 23, in resource "docker_image":
  23: resource "docker_image" {

All resource blocks must have 2 labels (type, name).
```
**Объяснение:** Ресурс был объявлен без имени. Все ресурсы должны содержать два идентификатора: тип и имя.

2. **Ошибка:**
```plaintext
Error: Invalid resource name
  on main.tf line 28, in resource "docker_container" "1nginx":
  28: resource "docker_container" "1nginx" {

A name must start with a letter or underscore and may contain only letters, digits, underscores, and dashes.
```
**Объяснение:** Имя ресурса "1nginx" начинается с цифры, что нарушает правила именования.

---

## Задание 5

![](https://github.com/V3l337/ter-homeworks_01/blob/main/docker%20ps.png)

---

## Задание 6

### Опасность применения ключа `-auto-approve`:
Ключ `-auto-approve` автоматически подтверждает выполнение изменений без запроса у пользователя. Это может быть опасно, так как:
- Неправильная конфигурация или опечатки могут привести к разрушению важных ресурсов.
- Возможно непреднамеренное создание или удаление инфраструктуры.

### Зачем используется ключ `-auto-approve`:
Этот ключ полезен в автоматизированных сценариях (например, в CI/CD пайплайнах), где требуется выполнение Terraform без вмешательства человека.

![](https://github.com/V3l337/ter-homeworks_01/blob/main/docker%20ps%20%2B%20.png)

---

## Задание 7

### Содержимое файла `terraform.tfstate` после удаления ресурсов:
```json
{
  "version": 4,
  "terraform_version": "1.10.4",
  "serial": 13,
  "lineage": "15567b64-9a41-bead-7b54-8219f99f8e9f",
  "outputs": {},
  "resources": [],
  "check_results": null
}
```

---

## Задание 8

### Почему не был удалён Docker-образ `nginx:latest`:
Docker-образ остался на хосте из-за настройки:
```hcl
keep_locally = true
```
**Подтверждение из документации:**
> **keep_locally** (Optional) If true, then the Docker image won't be removed on resource destroy.

