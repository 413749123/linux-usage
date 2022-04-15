### Linux-Shell常用代码记录

#### 常用方法
1. 命令行带颜色日志:
    ```bash
    #!/usr/bin/env bash

    setup_color() {
      # Only use colors if connected to a terminal
      RED=$(printf '\033[31m')
      GREEN=$(printf '\033[32m')
      YELLOW=$(printf '\033[33m')
      BLUE=$(printf '\033[34m')
      BOLD=$(printf '\033[1m')
      RESET=$(printf '\033[m')
    }

    log_err() {
      printf '[%s  ERR %s] ==> %s\n' "$BOLD$RED" "$RESET" "$*" >&2
    }

    log_ok() {
      printf '[%s  OK  %s] ==> %s\n' "$GREEN" "$RESET" "$*" >&2
    }

    log_warn() {
      printf '[%s WARN %s] ==> %s\n' "$YELLOW" "$RESET" "$*" >&2
    }

    log_info() {
      printf '[%s INFO %s] ==> %s\n' "$BLUE" "$RESET" "$*" >&2
    }

    setup_color
    ```
2. 判断命令是否存在:
    ```bash
    #!/bin/env bash
    command_exists() {
      command -v "$@" >/dev/null 2>&1
    }

    command_exists git || {
      echo 'git not exists!'
      exit 1
    }

    if ! command_exiss git ; then
      echo 'git not exists!'
    fi
    ```