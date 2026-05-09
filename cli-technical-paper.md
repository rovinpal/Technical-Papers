# Command Line Interface (CLI) – Quick Guide


## Introduction

The command line is a way to talk to the computer by typing commands instead of using a mouse. You type instructions into a shell, which passes them to the operating system. CLI is faster for many tasks, works on remote systems, and lets you automate things easily.


# What is a Shell?

* Shell is basically a program that takes commands you type and talks to the OS kernel.
* It’s not the kernel itself.
* Starts when you log in or open a terminal.
* Common shells in Linux:
  * BASH – Most common, open source.
  * CSH – Like C language syntax.
  * KSH – POSIX standard base.
  * TCSH – Enhanced CSH.


# Unix Philosophy

* Do one thing and do it well.
* Everything is a file.
* Text files for data/config.
* Automate with shell scripts.
* Chain commands with pipes.
* Portability > efficiency.


# Linux Directory Structure

* / – Root folder
* /bin – Essential programs (ls, bash, cp)
* /sbin – Admin programs (disk/network tools)
* /etc – System-wide config files
* /home – User folders (/home/bob)
* /root – Root user home
* /usr – User apps, libraries (/usr/bin, /usr/lib)
* /tmp – Temporary files
* /var – Variable files (logs, mail)
* /opt – Optional software


# CLI Basic Commands

## File operations:

* ls – list files
* cd – change directory
* cp – copy files
* mv – move or rename files
* rm – remove files

## File viewing & editing:

* cat, less, head, tail – view file contents
* nano, vi – edit files

## Text processing:

* grep – search text
* sort – sort lines
* uniq – remove duplicates
* wc – count lines, words, characters

## Pipes & redirection:

* | – send output of one command to another
* > – overwrite output to a file
* >> – append output to a file
* < – read input from a file

## Processes
* ps – list processes
* top – live CPU/memory usage
* kill – stop processes (kill -9 = force stop)

## Networking
* ping – test connectivity
* ifconfig / ip – network interfaces
* ssh – remote shell
* curl / wget – download files
* netstat / ss – active connections

## References

* https://en.wikipedia.org/wiki/Unix_philosophy
* https://www.youtube.com/watch?v=D-VqgvBMV7g
* https://www.youtube.com/watch?v=BmVmJi5dR9c
* https://www.youtube.com/watch?v=Bzd7XfApxLI
* https://www.youtube.com/watch?v=VgbnndezHbw
* https://neilkakkar.com/unix.html
