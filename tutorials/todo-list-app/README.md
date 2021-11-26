---
description: >-
  In this tutorial we're going to be creating a simple TODO application in
  Avalonia using the Model-View-ViewModel (MVVM) pattern.
---

# 📋 ToDo List App

In this tutorial we're going to be creating a simple TODO application in Avalonia using the Model-View-ViewModel \(MVVM\) pattern.

{% hint style="info" %}
You can find the code for the completed application [here](https://github.com/grokys/todo-tutorial).
{% endhint %}

![The finished application](../../.gitbook/assets/image%20%2814%29.png)

## Model-View-ViewModel \(MVVM\) <a id="model-view-viewmodel-mvvm"></a>

We're going to be using the [Model-View-ViewModel pattern \(MVVM\)](https://docs.avaloniaui.net/guides/basics/mvvm) for this tutorial. MVVM is a common pattern used for writing GUI applications, and is the recommended pattern to use when writing Avalonia applications. We'll be assuming a [CRUD](https://en.wikipedia.org/wiki/Create,_read,_update_and_delete) application here, but most of these concepts can be applied to all types of applications.

{% hint style="warning" %}
For this guide we're going to be using [ReactiveUI](https://reactiveui.net/) which is a MVVM framework based on [.NET Reactive Extensions](https://reactivex.io/). This guide will explain how to use MVVM and ReactiveUI with Avalonia but you can also see the [ReactiveUI documentation](https://reactiveui.net/docs/) for more detailed information.
{% endhint %}

