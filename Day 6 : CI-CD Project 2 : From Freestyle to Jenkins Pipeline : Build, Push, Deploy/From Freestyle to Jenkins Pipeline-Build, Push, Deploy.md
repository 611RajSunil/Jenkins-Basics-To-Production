# Day 6: CI/CD Project 2: From Freestyle to Jenkins Pipeline: Build, Push, Deploy

## Table of Contents

* [Introduction](#introduction)  
* [Prerequisites](#prerequisites)  
* [Why Pipelines? (the big wins)](#why-pipelines-the-big-wins)  
  * [Pipeline Job vs Chained Freestyle](#pipeline-job-vs-chained-freestyle)  
  * [Pipeline vs Freestyle — Top 5](#pipeline-vs-freestyle--top-5)  
  * [Bottom line](#bottom-line)  
* [Two ways to use a Pipeline](#two-ways-to-use-a-pipeline)  
* [Groovy: how much do you need?](#groovy-how-much-do-you-need)  
* [Declarative Pipeline — the core building blocks](#declarative-pipeline--the-core-building-blocks)  
  * [Minimal shape](#minimal-shape)  
  * [What each block means](#what-each-block-means)  
  * [Useful companions you’ll meet shortly](#useful-companions-youll-meet-shortly)  
* [Create a Skeleton Jenkinsfile](#create-a-skeleton-jenkinsfile)  
* [Build a Production-grade Jenkinsfile (replicates Day-5)](#build-a-production-grade-jenkinsfile-replicates-day-5)  
  * [Step 1: Add credentials via the Snippet Generator](#step-1-add-credentials-via-the-snippet-generator)  
  * [Step 2: Define reusable environment variables](#step-2-define-reusable-environment-variables)  
  * [Step 3: Full Jenkinsfile (simple, clear, production-ish)](#step-3-full-jenkinsfile-simple-clear-production-ish)  
* [Improving our Day-5 flow with a Jenkinsfile](#improving-our-day-5-flow-with-a-jenkinsfile)  
  * [1) Use Pipeline Script from SCM (so checkout happens automatically)](#1-use-pipeline-script-from-scm-so-checkout-happens-automatically)  
  * [2) Post actions](#2-post-actions)  
  * [3) Generate and archive deploy-info.txt](#3-generate-and-archive-deploy-infottxt)  
  * [4) Clean the workspace](#4-clean-the-workspace)  
  * [Consolidated Jenkinsfile (simple + improvements)](#consolidated-jenkinsfile-simple--improvements)  
* [Conclusion](#conclusion)  
* [References](#references)  

---

## Introduction

Today we’ll convert our Freestyle flow into a **Jenkinsfile**: same steps (checkout → build → push → deploy → test), but now **as code** so it’s versioned, reviewable, and easy to evolve. We’ll keep the core simple (build number as the image tag), then add practical upgrades: **post actions**, a **deploy-info.txt** artifact for traceability, and a final **workspace cleanup**. By the end, you’ll have a production-shaped pipeline that’s still beginner-friendly.

---

## Prerequisites

Before Day 6, make sure you’re comfortable with the Day-5 flow (Docker-outside-of-Docker, credentials, build → push → deploy → test).
Review these:

* **Day 5 — GitHub Notes:** [Day 5 : Jenkins Project 1 : Build, Push & Run a Flask App with Jenkins](https://github.com/611RajSunil/Jenkins-Basics-To-Production/tree/main/Day%205%20%3A%20Jenkins%20Project%201%20%3A%20Build%2C%20Push%20%26%20Run%20a%20Flask%20App%20with%20Jenkins)
