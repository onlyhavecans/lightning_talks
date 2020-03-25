# My Favorite
# Programming Serpents
_That are not python_

---

## A Golang talk

---

## How do I Golang?

---

## vim main.go

---

## No wait but how do I make a maintanable Golang?

---

- /cli/actual_main.go
- /bin/probably_important.go
- /server/run_this.go
- /lib/errors.go
- /lib/logging.go
- /lib/config.go
- /lib/config_butonlyforactualmain.go
- /Makefile

---

# UGH

---

## An Alternitive

---

# Cobra & Viper

---

# Step 1: Cobra

---

## cobra init .

---

- main.go - Do not touch me
- cmd/root.go
- cmd/server.go
- cmd/cert.go
- lib/**

---

## Where is my makefile?

---

## go build .

---

## One binary:
redirector

## Many sub commands:
redirector
redirector server
redirector cert

---

## Sounds like config hell

---

# Step 2: Viper

---

## Who wants to parse & merge;
## Config file
## Flags
## Env

---

```golang
// vim config.toml

viper.SetConfigName("config")
viper.AddConfigPath("/etc/app/")
viper.AddConfigPath(".")

viper.SetDefault("https_port", 8443)

err := viper.ReadInConfig()
port := viper.GetInt("https_port")
```

---

## Wait you didn't tell viper it was a toml file

---

## Viper will figure it out

---

## What about my ENV?

---

```golang
// export REDIRECTOR_HTTPS_PORT=443

viper.SetEnvPrefix("REDIRECTOR_")
viper.AutomaticEnv()
port := viper.GetInt("https_port")
```

---

## And my command line flags?!

---

```golang
// redirector --https 443

serverCmd.Flags().Int("https", 443, "Port to run https on")
viper.BindPFlag("https_port", serverCmd.Flags().Lookup("https"))
```

---

### So you are telling me these two will handle my application's structure, all my configuration management, and allow for well isolated components of my application to be run seperately?

---

# Yes

---

# Questions?

---

## Wait I have a question!

---

## Do I have to use both?

---

# No way!
For very simple apps I only use viper

I have used Cobra without Viper once, but almost everything I write needs a config

---

# Any More Questions?
