# Run RYU SDN via docker

## How to run

### use alias

setup alias add this line below to your `~/.bashrc` or `~/.zshrc` or just run in your terminal

```bash
alias ryu-manager="docker run -it --rm -v .:/run --net=host --name ryu arikato111/ryu"
```

run RYU

```
ryu-manager ryu.app.simple_switch_13
```

### Or run directly via docker command

```
docker run -it --rm -v .:/run --net=host --name ryu arikato111/ryu
```
