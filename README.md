# Rede Language Design

![Discord Shield](https://discordapp.com/api/guilds/1036138273476722778/widget.png?style=shield) [![Contributor Covenant](https://img.shields.io/badge/Contributor%20Covenant-2.1-4baaaa.svg)](code_of_conduct.md)

Welcome! This repo is dedicated to the design of the Rede language. New Rede language features are considered, defined, and specified here.

## What is in this repo?

- The full language specifications for all released versions.
- The potential language specifications for all versions currently under consideration (called "drafts").
- A summary of the language version history.

The language is implemented in the rede-org/language-dev repo, based upon the design specifications outlined here.

## What is Rede?

Rede (REactive Data Evaluation), pronounced the same as "reed" and "read", is the first Contextual Programming language. In accordance with Contextual Programming, Rede code is entirely data-driven with runtime logic determined by the data of the application. Reders (Rede devs) define data as contexts and logic as operations to occur when contextual conditions upon those operations are met. Operations can be encapsulated within behaviors, which provide soft-bindings between the contexts and limit the exposure of their operations.

## What are the Goals of Rede?

**Proper Rede code is redeable** (pun intended)<br>Rede emphasizes readability, striving to be close to natural language when reasonable.

**Redeing with 'when'** ('Redeing' here meaning to read/write Rede code)<br>As opposed to 'how' or 'what', Rede focuses on coding from 'when', which lets Rede abstract away the concerns of parallelism and make control flow a quality of the data instead of a means to structure logic. Rede code architecture can be largely described through statements that start with 'when'.

**Rede for fast, secure, dynamic applications**<br>Rede code is entirely data-driven and composition-based. This enables better performance through effective data management and automated threading, the elimination of ambiguity by removing 'null' and inheritance, the reduction of coupling between logic, and inherent support for dynamic systems of functionality.

## Why do we need Rede?

Application development continues to become more complex and demanding, particularly for applications whose users demand a high-degree of customizations, regular changes, and/or dynamic interactivity (such as video games and similar applications). Current programming languages and their associated practices do not scale well to meet these demands, neither in terms of how they can be developed nor in achieving the desired results. Rede aims to address this by introducing code that can be developed more effectively in general and that enables the easier creation/maintenance of these kinds of applications.

## Want to Help?

A process for evaluating language feature proposals will be set up after version 1 has been released. For now, if you would like to contribute please [email us](mailto:lucas@lucasstertz.com).
