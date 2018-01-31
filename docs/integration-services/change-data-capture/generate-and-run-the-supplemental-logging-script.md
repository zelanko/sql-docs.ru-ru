---
title: "Создание и запуск скрипта дополнительного журналирования | Документы Майкрософт"
ms.custom: 
ms.date: 03/01/2017
ms.prod: sql-non-specified
ms.prod_service: integration-services
ms.service: 
ms.component: change-data-capture
ms.reviewer: 
ms.suite: sql
ms.technology:
- integration-services
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- supLog
ms.assetid: 6e940d93-12c6-4cda-9333-5489b245f0e4
caps.latest.revision: 
author: douglaslMS
ms.author: douglasl
manager: craigg
ms.workload: Inactive
ms.openlocfilehash: ee20cd83df04d4ec3929f9ee39068969c0d18950
ms.sourcegitcommit: 9e6a029456f4a8daddb396bc45d7874a43a47b45
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 01/25/2018
---
# <a name="generate-and-run-the-supplemental-logging-script"></a>Создание и запуск скрипта дополнительного журналирования
  Страница «Настройка таблиц для отслеживания изменений» служит для запуска в базе данных-источнике Oracle скрипта для задания дополнительного журналирования.  
  
 **Запуск скриптов дополнительного журналирования**  
  
 Нажмите кнопку **Выполнить скрипт** , чтобы запустить скрипт дополнительного журналирования в таблицах, определенных для экземпляра CDC. Этот скрипт настраивает базу данных Oracle таким образом, что все интересующие столбцы будут записываться в журналы транзакций базы данных при регистрации операций UPDATE для отслеживаемых таблиц. Как правило, этот скрипт проверяет и выполняет системный администратор Oracle.  
  
 Скрипт также можно выполнить вручную с помощью программы SQL*Plus.  
  
 **Запуск скрипта вручную**  
  
 Щелкните **Копировать** , чтобы скопировать скрипт в буфер обмена. Запустите программу SQL*Plus и перейдите в каталог с базой данных-источником Oracle. Вставьте скрипт в SQL\*Plus, чтобы выполнить его.  
  
 Чтобы сохранить скрипт дополнительного журналирования в текстовый файл, щелкните **Сохранить как** и перейдите в каталог, куда необходимо сохранить файл. Введите имя файла и нажмите кнопку **Сохранить** , чтобы сохранить файл.  
  
 Нажмите кнопку **Далее** , чтобы перейти на страницу [Generate Mirror Tables and CDC Capture Instances](../../integration-services/change-data-capture/generate-mirror-tables-and-cdc-capture-instances.md).  
  
## <a name="see-also"></a>См. также:  
 [Как создать экземпляр изменения базы данных SQL Server](../../integration-services/change-data-capture/how-to-create-the-sql-server-change-database-instance.md)   
 [Обзор и создание скриптов дополнительного журналирования](../../integration-services/change-data-capture/review-and-generate-supplemental-logging-scripts.md)  
  
  
