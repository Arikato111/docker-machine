# Run RYU SDN via docker

## How to run

### use alias

setup alias

```bash
alias ryu-manager="docker run -it --rm --net=host --name ryu arikato111/ryu"
```

run RYU

```
ryu-manager ryu.app.simple_switch_13
```

### Or run directly via docker command

```
docker run -it --rm --net=host --name ryu arikato111/ryu
```