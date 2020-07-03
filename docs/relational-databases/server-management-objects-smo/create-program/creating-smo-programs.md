---
title: Создание программ SMO | Документация Майкрософт
ms.custom: ''
ms.date: 03/14/2017
ms.prod: sql
ms.prod_service: database-engine
ms.reviewer: ''
ms.technology: ''
ms.topic: reference
helpviewer_keywords:
- Visual Basic [SMO]
- Visual C# [SMO]
- programming [SMO]
- SQL Server Management Objects, programming
- SMO [SQL Server], programming
ms.assetid: 7d2f0bcf-f1ae-45b8-bc3f-7aea4fae7e45
author: markingmyname
ms.author: maghan
monikerRange: =azuresqldb-current||=azure-sqldw-latest||>=sql-server-2016||=sqlallproducts-allversions||>=sql-server-linux-2017||=azuresqldb-mi-current
ms.openlocfilehash: fd92f97c8f73b650108b7b09f14d97268082ffd3
ms.sourcegitcommit: f7ac1976d4bfa224332edd9ef2f4377a4d55a2c9
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 07/02/2020
ms.locfileid: "85883622"
---
# <a name="creating-smo-programs"></a>Создание приложений SMO
[!INCLUDE [SQL Server ASDB, ASDBMI, ASDW ](../../../includes/applies-to-version/sql-asdb-asdbmi-asdw.md)]

  Общее программирование объектов [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] SMO включает в себя аспекты, общие для всех объектов (запуск методов, задание значений свойств, работа с коллекциями).   
  
|Раздел|Описание|  
|-----------|-----------------|  
|[Соединение с экземпляром SQL Server](../../../relational-databases/server-management-objects-smo/create-program/connecting-to-an-instance-of-sql-server.md)|Простейшая программа SMO, которая производит соединение с экземпляром [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)]. Демонстрирует проверку подлинности Windows и проверку подлинности [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)]. Содержит также фрагменты кода, демонстрирующие соединение с локальным и удаленным экземплярами [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)].|  
|[Отсоединение от экземпляра SQL Server](../../../relational-databases/server-management-objects-smo/create-program/disconnecting-from-an-instance-of-sql-server.md)|Программа демонстрирует отключение от соединения с экземпляром [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)].|  
|[Вызов методов](../../../relational-databases/server-management-objects-smo/create-program/calling-methods.md)|В этом разделе приводится описание общего подхода к вызову методов. Демонстрируется использование параметров, а также обработка таблиц с данными, возвращенных в объекте <xref:System.Data.DataTable>. Также содержит пример вызова конструктора объекта и вызова метода **clone** .|  
|[Установка свойств в SMO](../../../relational-databases/server-management-objects-smo/create-program/setting-properties-smo.md)|В этом разделе описывается настройка различных типов свойств. Описывает, как задать и получить значение свойства объекта. Содержит также примеры задания свойств объекта при его создании и итерации по всем свойствам объекта.|  
|[Использование коллекций](../../../relational-databases/server-management-objects-smo/create-program/using-collections.md)|Различные программы, в которых обсуждаются технические вопросы работы с коллекциями объектов.  Показывает, как ссылаться на объект с помощью коллекций. Включает также пример итерации по членам коллекции. |  
|[Обработка событий SMO](../../../relational-databases/server-management-objects-smo/create-program/handling-smo-events.md)|В этом разделе описываются особенности настройки и обработки событий в SMO. Содержит пример кода, показывающий, как установить обработчик события и настроить подписку на события.|  
|[Обработка исключений SMO](../../../relational-databases/server-management-objects-smo/create-program/handling-smo-exceptions.md)|В этом разделе описываются способы обработки исключений в SMO. Включает примеры перехвата исключения и вывода внутреннего исключения. |  
|[Работа с типами данных](../../../relational-databases/server-management-objects-smo/create-program/working-with-data-types.md)|В этом разделе описана работа с различными типами данных [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)]. Описывается создание типа данных со спецификацией в конструкторе объекта.  Включает также пример создания типа данных с использованием конструктора по умолчанию.|  
|[Использование транзакций](../../../relational-databases/server-management-objects-smo/create-program/using-transactions.md)|В этом разделе описываются способы обработки транзакций в программе SMO. Включены примеры использования транзакций в программе SMO.|  
|[Использование режима записи](../../../relational-databases/server-management-objects-smo/create-program/using-capture-mode.md)|В данном разделе рассказывается, как организовать запись вывода программы SMO. Приводится пример, в котором программа SMO в виде инструкций [!INCLUDE[tsql](../../../includes/tsql-md.md)] посылается экземпляру [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] для последующего выполнения.|  
  
  
