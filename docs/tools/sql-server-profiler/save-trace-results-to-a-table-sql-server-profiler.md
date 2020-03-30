---
title: Сохранение результатов трассировки в таблице
titleSuffix: SQL Server Profiler
ms.prod: sql
ms.prod_service: sql-tools
ms.reviewer: ''
ms.technology: profiler
ms.topic: conceptual
ms.assetid: edbecf74-683b-4e43-a1ef-7a3d5f5e27f6
author: markingmyname
ms.author: maghan
ms.custom: seo-lt-2019
ms.date: 03/14/2017
ms.openlocfilehash: 6fb406988c9aeb92e7f0c1d3689e5b513a7ea0d3
ms.sourcegitcommit: ff82f3260ff79ed860a7a58f54ff7f0594851e6b
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 03/29/2020
ms.locfileid: "75307432"
---
# <a name="save-trace-results-to-a-table-sql-server-profiler"></a>сохранять результаты трассировки в таблицу (SQL Server Profiler)

[!INCLUDE[appliesto-ss-xxxx-xxxx-xxx-md](../../includes/appliesto-ss-xxxx-xxxx-xxx-md.md)]

В этом подразделе описывается, как сохранять результаты трассировок в таблицу базы данных с помощью приложения [!INCLUDE[ssSqlProfiler](../../includes/sssqlprofiler-md.md)].  
  
## <a name="to-save-trace-results-to-a-table"></a>Сохранение результатов трассировки в таблицу
  
1.  В меню **Файл** выберите пункт **Создать трассировку**, а затем подключитесь к экземпляру [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)].  
  
     Отображается диалоговое окно **Свойства трассировки**.  
  
    > [!NOTE]  
    >  Если установлен параметр **Начать трассировку немедленно после установления соединения**, диалоговое окно **Свойства трассировки**не отображается, а вместо этого начинается трассировка. Чтобы отключить этот параметр, в меню **Сервис**выберите пункт **Параметры**и снимите флажок **Начать трассировку немедленно после установления соединения** .  
  
2.  В поле **Имя трассировки** введите имя трассировки и нажмите кнопку **Сохранить в таблицу**.  
  
3.  В диалоговом окне **Соединение с сервером** подключитесь к содержащей таблицу трассировок базе данных [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] .  
  
4.  В диалоговом окне **Целевая таблица** выберите базу данных из списка **База данных**.  
  
5.  В списке **Владелец** выберите владельца трассировки.  
  
6.  В списке **Таблица** введите или выберите имя таблицы для сохранения результатов трассировки. Нажмите кнопку **ОК.**  
  
7.  В диалоговом окне **Свойства трассировки** установите флажок **Максимальное число строк (тыс.)** , чтобы задать максимальное число строк для сохранения.  
  
## <a name="see-also"></a>См. также:  
 [Приложение SQL Server Profiler](../../tools/sql-server-profiler/sql-server-profiler.md)  
  
  
