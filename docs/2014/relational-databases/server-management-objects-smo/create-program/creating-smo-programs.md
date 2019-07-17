---
title: Создание приложений SMO | Документация Майкрософт
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
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
author: stevestein
ms.author: sstein
manager: craigg
ms.openlocfilehash: ccf26cf30c53e3a336e842cbbffc1ff517075fef
ms.sourcegitcommit: 3026c22b7fba19059a769ea5f367c4f51efaf286
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 06/15/2019
ms.locfileid: "68198004"
---
# <a name="creating-smo-programs"></a>Создание приложений SMO
  Общее программирование объектов [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] SMO включает в себя аспекты, общие для всех объектов (запуск методов, задание значений свойств, работа с коллекциями).  
  
|Раздел|Описание|  
|-----------|-----------------|  
|[Соединение с экземпляром SQL Server](connecting-to-an-instance-of-sql-server.md)|Простейшая программа SMO, которая производит соединение с экземпляром [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)]. Демонстрирует проверку подлинности Windows и проверку подлинности [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)]. Содержит также фрагменты кода, демонстрирующие соединение с локальным и удаленным экземплярами [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)].|  
|[Отсоединение от экземпляра SQL Server](disconnecting-from-an-instance-of-sql-server.md)|Программа демонстрирует отключение от соединения с экземпляром [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)].|  
|[Вызов методов](calling-methods.md)|В этом разделе приводится описание общего подхода к вызову методов. Демонстрируется использование параметров, а также обработка таблиц с данными, возвращенных в объекте <xref:System.Data.DataTable>. Содержит также примеры вызова конструктора объекта и метода `Clone`.|  
|[Установка свойств](setting-properties-smo.md)|В этом разделе описывается настройка различных типов свойств. Описывает, как задать и получить значение свойства объекта. Содержит также примеры задания свойств объекта при его создании и итерации по всем свойствам объекта.|  
|[Использование коллекций](using-collections.md)|Различные программы, в которых обсуждаются технические вопросы работы с коллекциями объектов. Показывает, как ссылаться на объект с помощью коллекций. Включает также пример итерации по членам коллекции.|  
|[Обработка событий SMO](handling-smo-events.md)|В этом разделе описываются особенности настройки и обработки событий в SMO. Содержит пример кода, показывающий, как установить обработчик события и настроить подписку на события.|  
|[Обработка исключений SMO](handling-smo-exceptions.md)|В этом разделе описываются способы обработки исключений в SMO. Включает примеры перехвата исключения и вывода внутреннего исключения.|  
|[Работа с типами данных](working-with-data-types.md)|В этом разделе описана работа с различными типами данных [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)]. Описывается создание типа данных со спецификацией в конструкторе объекта. Включает также пример создания типа данных с использованием конструктора по умолчанию.|  
|[Использование транзакций](using-transactions.md)|В этом разделе описываются способы обработки транзакций в программе SMO. Включены примеры использования транзакций в программе SMO.|  
|[Использование режима записи](using-capture-mode.md)|В данном разделе рассказывается, как организовать запись вывода программы SMO. Приводится пример, в котором программа SMO в виде инструкций [!INCLUDE[tsql](../../../includes/tsql-md.md)] посылается экземпляру [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] для последующего выполнения.|  
  
  
