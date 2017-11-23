---
title: "Создание приложений SMO | Документы Microsoft"
ms.custom: 
ms.date: 03/14/2017
ms.prod: sql-non-specified
ms.prod_service: database-engine
ms.service: 
ms.component: smo
ms.reviewer: 
ms.suite: sql
ms.technology: docset-sql-devref
ms.tgt_pltfrm: 
ms.topic: reference
helpviewer_keywords:
- Visual Basic [SMO]
- Visual C# [SMO]
- programming [SMO]
- SQL Server Management Objects, programming
- SMO [SQL Server], programming
ms.assetid: 7d2f0bcf-f1ae-45b8-bc3f-7aea4fae7e45
caps.latest.revision: "34"
author: JennieHubbard
ms.author: jhubbard
manager: jhubbard
ms.workload: On Demand
ms.openlocfilehash: cd8d9fa33596bd200816c7d2e65213646c9e8344
ms.sourcegitcommit: 44cd5c651488b5296fb679f6d43f50d068339a27
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 11/17/2017
---
# <a name="creating-smo-programs"></a>Создание приложений SMO
[!INCLUDE[appliesto-ss-xxxx-xxxx-xxx-md](../../../includes/appliesto-ss-xxxx-xxxx-xxx-md.md)]Общее программирование объектов [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] управляющих объектов (SMO) объектов включает общие области, которые совместно используют все объекты, такие как запуск методов, задание свойств, коллекций и управление ими.  
  
|Раздел|Description|  
|-----------|-----------------|  
|[Соединение с экземпляром SQL Server](../../../relational-databases/server-management-objects-smo/create-program/connecting-to-an-instance-of-sql-server.md)|Простейшая программа SMO, которая производит соединение с экземпляром [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)]. Демонстрирует проверку подлинности Windows и проверку подлинности [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)]. Содержит также фрагменты кода, демонстрирующие соединение с локальным и удаленным экземплярами [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)].|  
|[Отсоединение от экземпляра SQL Server](../../../relational-databases/server-management-objects-smo/create-program/disconnecting-from-an-instance-of-sql-server.md)|Программа демонстрирует отключение от соединения с экземпляром [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)].|  
|[Вызов методов](../../../relational-databases/server-management-objects-smo/create-program/calling-methods.md)|В этом разделе приводится описание общего подхода к вызову методов. Демонстрируется использование параметров, а также обработка таблиц с данными, возвращенных в объекте <xref:System.Data.DataTable>. Включает также пример способы вызова конструктора объекта и вызвать **клон** метод.|  
|[Установка свойств в SMO](../../../relational-databases/server-management-objects-smo/create-program/setting-properties-smo.md)|В этом разделе описывается настройка различных типов свойств. Описывает, как задать и получить значение свойства объекта. Содержит также примеры задания свойств объекта при его создании и итерации по всем свойствам объекта.|  
|[Использование коллекций](../../../relational-databases/server-management-objects-smo/create-program/using-collections.md)|Различные программы, в которых обсуждаются технические вопросы работы с коллекциями объектов.  Показывает, как ссылаться на объект с помощью коллекций. Включает также пример итерации по членам коллекции. |  
|[Обработка событий SMO](../../../relational-databases/server-management-objects-smo/create-program/handling-smo-events.md)|В этом разделе описываются особенности настройки и обработки событий в SMO. Содержит пример кода, показывающий, как установить обработчик события и настроить подписку на события.|  
|[Обработка исключений SMO](../../../relational-databases/server-management-objects-smo/create-program/handling-smo-exceptions.md)|В этом разделе описываются способы обработки исключений в SMO. Включает примеры перехвата исключения и вывода внутреннего исключения. |  
|[Работа с типами данных](../../../relational-databases/server-management-objects-smo/create-program/working-with-data-types.md)|В этом разделе описана работа с различными типами данных [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)]. Описывается создание типа данных со спецификацией в конструкторе объекта.  Включает также пример создания типа данных с использованием конструктора по умолчанию.|  
|[Использование транзакций](../../../relational-databases/server-management-objects-smo/create-program/using-transactions.md)|В этом разделе описываются способы обработки транзакций в программе SMO. Включены примеры использования транзакций в программе SMO.|  
|[Использование режима записи](../../../relational-databases/server-management-objects-smo/create-program/using-capture-mode.md)|В данном разделе рассказывается, как организовать запись вывода программы SMO. Приводится пример, в котором программа SMO в виде инструкций [!INCLUDE[tsql](../../../includes/tsql-md.md)] посылается экземпляру [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] для последующего выполнения.|  
  
  
