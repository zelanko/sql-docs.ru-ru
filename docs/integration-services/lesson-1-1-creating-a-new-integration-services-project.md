---
title: Шаг 1. Создание нового проекта служб Integration Services | Документация Майкрософт
ms.custom: ''
ms.date: 01/03/2019
ms.prod: sql
ms.prod_service: integration-services
ms.reviewer: ''
ms.technology: integration-services
ms.topic: tutorial
ms.assetid: f14521b5-941e-443b-8f5e-385f98e37fbf
author: janinezhang
ms.author: janinez
manager: craigg
ms.openlocfilehash: 82420ce073f65483043d44670fc538849a447d90
ms.sourcegitcommit: 3026c22b7fba19059a769ea5f367c4f51efaf286
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 06/15/2019
ms.locfileid: "65723316"
---
# <a name="lesson-1-1-create-a-new-integration-services-project"></a>Урок 1-1. Создание нового проекта служб Integration Services

[!INCLUDE[ssis-appliesto](../includes/ssis-appliesto-ssvrpluslinux-asdb-asdw-xxx.md)]



Первым шагом создания пакета в службах [!INCLUDE[ssISnoversion](../includes/ssisnoversion-md.md)] будет создание проекта служб [!INCLUDE[ssISnoversion](../includes/ssisnoversion-md.md)] . Этот пример проекта содержит шаблоны для источников данных, представлений источников данных и пакетов, которые составляют решение для преобразования данных.  
  
Пакеты, которые вы создадите в этом учебнике по службам [!INCLUDE[ssISnoversion](../includes/ssisnoversion-md.md)], преобразуют значения данных, зависящих от языковых стандартов. Если компьютер не настроен на использование регионального параметра **Английский (США)** , необходимо настроить в пакете дополнительные свойства. 

Для уроков со 2-го по 6-й применяются копии того пакета, который вы создадите в этом занятии.  
  
> [!NOTE]  
> Ознакомьтесь с [предварительными требованиями для урока 1](../integration-services/lesson-1-create-a-project-and-basic-package-with-ssis.md#prerequisites), если вы еще не сделали этого.

## <a name="create-a-new-integration-services-project"></a>Создание нового проекта служб Integration Services  
  
1.  В меню **Пуск** Windows найдите и выберите элемент **Visual Studio (SSDT)** .  
  
2.  В Visual Studio последовательно выберите **Файл** > **Новый** > **Проект**, чтобы создать новый проект [!INCLUDE[ssISnoversion](../includes/ssisnoversion-md.md)].  
  
3.  В диалоговом окне **Создать проект** разверните узел **Бизнес-аналитика** в категории **Установленные** и выберите **Проект служб Integration Services** на панели **Шаблоны**.  
  
4.  В поле **Имя** измените заданное по умолчанию имя на **Учебник по службам SQL Server Integration Services**. Чтобы использовать уже существующую папку, снимите флажок **Создать каталог для решения**.  
  
5.  Подтвердите местоположение по умолчанию или щелкните **Обзор**, чтобы найти нужную папку. В диалоговом окне **Расположение проекта** выберите папку и щелкните **Выбрать папку**.  
  
6.  Нажмите кнопку **ОК**.  
  
    По умолчанию создается пустой пакет с именем **Package.dtsx**, который добавляется в узел проекта **Пакеты служб SSIS**.  
  
7.  В **обозревателе решений** щелкните правой кнопкой мыши файл **Package.dtsx**, выберите действие **Переименовать**и присвойте пакету по умолчанию имя **Lesson 1.dtsx**.  
  
## <a name="go-to-next-task"></a>Переход к следующей задаче
[Шаг 2. Добавление и настройка диспетчера соединений с неструктурированными файлами](../integration-services/lesson-1-2-adding-and-configuring-a-flat-file-connection-manager.md)  
  
