---
title: "Первое решение"
date: 2020-04-15T06:52:37+06:00
draft: true
---

Среди наших знакомых есть известный спамер. В конце каждого контеста он сабмитит свои неправильные решения со скоростью пулемёта. Кроме того, он ещё и ведёт нечестную игру, всегда используя по несколько отладочных аккаунтов. Жюри наконец-то решило дисквалифицировать спамера. Для этого они сначала хотят определить все его отладочные аккаунты. Известно, какие команды сабмитили свои решения в последние 10 минут контеста. Ваша задача — найти все отладочные аккаунты спамера. Жюри считает аккаунтами спамера всех, кто сабмитил решения больше одного раза в последние 10 минут.

### Исходные данные

В первой строке записано число N — количество сабмитов в последние 10 минут (0 ≤ N ≤ 100). Следующие N строк содержат названия команд, сабмитивших решения. Названия состоят только из строчных латинских букв и цифр. Длина названий не превосходит 30 символов.


```golang
package main

import (
	"bufio"
	"fmt"
	//"math/big"
	"os"
	"strings"
)

func main() {
	f, _ := os.Open("input.txt")
	in := bufio.NewReader(f)
	//in := bufio.NewReader(os.Stdin)
	out := bufio.NewWriter(os.Stdout)
	text, _ := in.ReadString(0)
	a := strings.Fields(text)
	var b []string
	for i, s := range a {
		found := false
		for _, bs := range b {
			if bs == s {
				found = true
				break
			}
		}
		if !found {
			for j := i + 1; j <= len(a)-1; j++ {
				if s == a[j] {
					b = append(b, s)
					break
				}
			}
		}
	}
	for _, s := range b {
		fmt.Println(s)
	}
	out.Flush()
}

```
