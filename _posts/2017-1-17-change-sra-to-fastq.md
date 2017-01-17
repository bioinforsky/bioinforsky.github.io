---
layout: post
title: "将sra格式转成fastq格式"
date: "2017-1-17"
categories: 生信基础软件
tags: 生信
keywords: fastq-dump sra fastq
description: 如何将sra格式转成fastq格式
---

* content
{:toc}


sra是NCBI 推出的存储高通量数据的格式，而平常我们处理的多是fastq格式，故从ncbi下载数据多需要把sra 转成fastq。 从 http://trace.ncbi.nlm.nih.gov/Traces/sra/sra.cgi?cmd=show&f=software&m=software&s=software 直接下载CentOS Linux 64 bit architecture（相应平台文件），解压就可以用了。

-O 指定输出目录
–split-3 对于双末端测序，一定使用这个参数，将一个\*.sra文件转换成\*_1.fastq和\*_2.fastq两个文件，否则就会转换成一个\*.fastq文件，后续的分析会出错。
```bash
fastq-dump *.sra -O PATH  #单端
fastq-dump --split-3 *.sra -O PATH  #双端
```