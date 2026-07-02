# MGSettings

<!-- Badge opcional para deixar claro visualmente -->
![Status](https://img.shields.io/badge/status-arquivado--archived-red.svg)

> **Aviso importante:** Esta biblioteca foi **oficialmente arquivada** e não receberá mais atualizações, correções de bugs ou suporte para novas versões.

**MGSettings** é uma biblioteca leve em Go para **gerenciamento simples de configurações persistentes**, utilizando arquivos JSON armazenados automaticamente no diretório do usuário ou em um caminho customizado.

Ideal para aplicações CLI, desktop ou serviços que precisam salvar preferências sem dependências externas.

---

## ✨ Recursos

* 💾 Persistência automática em arquivo `config.json`
* 🏠 Suporte a diretório padrão no *Home* do usuário (`~/.appname`)
* 📁 Suporte a caminho customizado
* 🧩 API simples para tipos comuns
  * `string`
  * `int`
  * `bool`
  * `[]string`
* 🔄 Fallback automático para valores padrão
* 📦 Baseado apenas na biblioteca padrão do Go

---

## 📦 Instalação

```bash
go get github.com/mugomes/mgsettings
```

---

## 🚀 Uso básico

### Carregando configurações

```go
import "github.com/mugomes/mgsettings"

cfg, err := mgsettings.Load("meuapp", true)
if err != nil {
	log.Fatal(err)
}
```

Isso criará automaticamente:

```text
~/.meuapp/config.json
```

---

## ✍️ Salvando valores

```go
cfg.SetString("username", "joao")
cfg.SetInt("port", 8080)
cfg.SetBool("dark_mode", true)
cfg.SetStringSlice("languages", []string{"pt", "en"})

cfg.Save()
```

---

## 📖 Lendo valores com fallback

```go
user := cfg.GetString("username", "guest")
port := cfg.GetInt("port", 3000)
dark := cfg.GetBool("dark_mode", false)
langs := cfg.GetStringSlice("languages", []string{"en"})
```

Se a chave não existir, o valor padrão será retornado.

---

## 🧠 Como funciona

* As configurações são armazenadas internamente como `json.RawMessage`
* Cada valor é serializado individualmente
* O arquivo só é gravado quando `Save()` é chamado
* Tipos são preservados automaticamente

---

## 🧩 Estrutura do arquivo gerado

```json
{
  "username": "joao",
  "port": 8080,
  "dark_mode": true,
  "languages": [
    "pt",
    "en"
  ]
}
```

---

## 👤 Autor

**Murilo Gomes Julio**

🔗 [https://mugomes.github.io](https://mugomes.github.io)

📺 [https://youtube.com/@mugomesoficial](https://youtube.com/@mugomesoficial)

---

## License

Copyright (c) 2025-2026 Murilo Gomes Julio

Licensed under the [MIT](https://github.com/mugomes/mgsettings/blob/main/LICENSE) license.

All contributions to the MGSettings are subject to this license.
