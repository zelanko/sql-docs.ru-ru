---
title: Сохранение результатов трассировки в файл (приложение SQL Server Profiler) | Документы Майкрософт
ms.custom: ''
ms.date: 03/14/2017
ms.prod: sql-non-specified
ms.prod_service: sql-tools
ms.service: ''
ms.component: sql-server-profiler
ms.reviewer: ''
ms.suite: sql
ms.technology:
- database-engine
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- saving traces
- traces [SQL Server], saving
ms.assetid: ac528747-0c19-4f3d-96f5-44c762a4abed
caps.latest.revision: 23
author: stevestein
ms.author: sstein
manager: craigg
ms.workload: Inactive
ms.openlocfilehash: e62a693466ac0de9a7ce67e9bbcbeec1c17b7af3
ms.sourcegitcommit: b6116b434d737d661c09b78d0f798c652cf149f3
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 01/17/2018
---
# <a name="save-trace-results-to-a-file-sql-server-profiler"></a>сохранить результаты трассировки в файл (приложение SQL Server Profiler)
[!INCLUDE[appliesto-ss-xxxx-xxxx-xxx-md](../../includes/appliesto-ss-xxxx-xxxx-xxx-md.md)] В этом разделе описывается сохранение результатов трассировки в файл с помощью [!INCLUDE[ssSqlProfiler](../../includes/sssqlprofiler-md.md)].  
  
### <a name="to-save-trace-results-to-a-file"></a>Сохранение результатов трассировки в файл  
  
1.  В меню **Файл** выберите пункт **Создать трассировку**, а затем подключитесь к экземпляру [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)].  
  
     Отображается диалоговое окно **Свойства трассировки**.  
  
    > [!NOTE]  
    >  Если установлен параметр **Начать трассировку немедленно после установления соединения**, диалоговое окно **Свойства трассировки**не отображается, а вместо этого начинается трассировка. Чтобы отключить этот параметр, в меню **Сервис**выберите пункт **Параметры**и снимите флажок **Начать трассировку немедленно после установления соединения** .  
  
2.  В поле **Имя трассировки** введите имя трассировки.  
  
3.  Установите флажок **Сохранять в файл** .  
  
     Отображается диалоговое окно **Сохранить как**.  
  
4.  Укажите путь и имя файла в диалоговом окне **Сохранить как**. Нажмите кнопку **Сохранить.**  
  
    > [!NOTE]  
    >  Убедитесь, что служба SQL Server обладает достаточными разрешениями для записи в файл в указанном каталоге.  
  
5.  В диалоговом окне **Свойства трассировки** введите максимальный размер файла в поле **Максимальный размер файла (МБ)** . Значение по умолчанию — 5 мегабайт.  
  
6.  При необходимости укажите следующие необязательные параметры:  
  
    -   Установите флажок **Включить операцию переключения на файл продолжения** , чтобы [!INCLUDE[ssSqlProfiler](../../includes/sssqlprofiler-md.md)] создавал новые файлы данных трассировки при достижении максимального размера файла. Этот параметр выбран по умолчанию.  
  
    -   Установите флажок **Данные трассировки серверных процессов** , чтобы гарантировать, что сервер сохранит данные обо всех событиях трассировки.  
  
        > [!NOTE]  
        >  Когда флажок **Данные трассировки серверных процессов**снят, сервер не записывает события, если запись событий привела бы к существенному понижению производительности.  
  
## <a name="see-also"></a>См. также:  
 [Приложение SQL Server Profiler](../../tools/sql-server-profiler/sql-server-profiler.md)  
  
  
