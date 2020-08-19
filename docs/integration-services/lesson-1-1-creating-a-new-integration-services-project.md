---
description: Урок 1-1. Создание нового проекта служб Integration Services
title: Шаг 1. Создание нового проекта служб Integration Services | Документация Майкрософт
ms.custom: ''
ms.date: 01/03/2019
ms.prod: sql
ms.prod_service: integration-services
ms.reviewer: ''
ms.technology: integration-services
ms.topic: tutorial
ms.assetid: f14521b5-941e-443b-8f5e-385f98e37fbf
author: chugugrace
ms.author: chugu
ms.openlocfilehash: 575353cd2cf770ed42d439fd31647ccaef3e01bd
ms.sourcegitcommit: e700497f962e4c2274df16d9e651059b42ff1a10
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 08/17/2020
ms.locfileid: "88449759"
---
# <a name="lesson-1-1-create-a-new-integration-services-project"></a>Урок 1-1. Создание нового проекта служб Integration Services

[!INCLUDE[sqlserver-ssis](../includes/applies-to-version/sqlserver-ssis.md)]



Первым шагом создания пакета в службах [!INCLUDE[ssISnoversion](../includes/ssisnoversion-md.md)] будет создание проекта служб [!INCLUDE[ssISnoversion](../includes/ssisnoversion-md.md)] . Этот пример проекта содержит шаблоны для источников данных, представлений источников данных и пакетов, которые составляют решение для преобразования данных.  
  
Пакеты, которые вы создадите в этом учебнике по службам [!INCLUDE[ssISnoversion](../includes/ssisnoversion-md.md)], преобразуют значения данных, зависящих от языковых стандартов. Если компьютер не настроен на использование регионального параметра **Английский (США)**, необходимо настроить в пакете дополнительные свойства. 

Для уроков со 2-го по 6-й применяются копии того пакета, который вы создадите в этом занятии.  
  
> [!NOTE]  
> Ознакомьтесь с [предварительными требованиями для урока 1](../integration-services/lesson-1-create-a-project-and-basic-package-with-ssis.md#prerequisites), если вы еще не сделали этого.

## <a name="create-a-new-integration-services-project"></a>Создание нового проекта служб Integration Services  
  
1.  В меню **Пуск** Windows найдите и выберите элемент **Visual Studio (SSDT)**.  
  
2.  В Visual Studio последовательно выберите **Файл** > **Новый** > **Проект**, чтобы создать новый проект [!INCLUDE[ssISnoversion](../includes/ssisnoversion-md.md)].  
  
3.  В диалоговом окне **Создать проект** разверните узел **Бизнес-аналитика** в категории **Установленные** и выберите **Проект служб Integration Services** на панели **Шаблоны**.  
  
4.  В поле **Имя** измените заданное по умолчанию имя на **Учебник по службам SQL Server Integration Services**. Чтобы использовать уже существующую папку, снимите флажок **Создать каталог для решения**.  
  
5.  Подтвердите местоположение по умолчанию или щелкните **Обзор**, чтобы найти нужную папку. В диалоговом окне **Расположение проекта** выберите папку и щелкните **Выбрать папку**.  
  
6.  Щелкните **ОК**.  
  
    По умолчанию создается пустой пакет с именем **Package.dtsx**, который добавляется в узел проекта **Пакеты служб SSIS**.  
  
7.  В **обозревателе решений** щелкните правой кнопкой мыши файл **Package.dtsx**, выберите действие **Переименовать**и присвойте пакету по умолчанию имя **Lesson 1.dtsx**.  
  
## <a name="go-to-next-task"></a>Переход к следующей задаче
[Шаг 2. Добавление и настройка диспетчера соединений с неструктурированными файлами](../integration-services/lesson-1-2-adding-and-configuring-a-flat-file-connection-manager.md)  
  
