---
title: Копирование удаленных таблиц
description: Использование функции копирования удаленных таблиц в хранилище Parallel Data System для платформы аналитики.
author: mzaman1
ms.prod: sql
ms.technology: data-warehouse
ms.topic: conceptual
ms.date: 04/17/2018
ms.author: murshedz
ms.reviewer: martinle
ms.custom: seo-dt-2019
ms.openlocfilehash: ecbbdced731e940de46dbde4a65adc486f602c2f
ms.sourcegitcommit: b87d36c46b39af8b929ad94ec707dee8800950f5
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/08/2020
ms.locfileid: "74400483"
---
# <a name="remote-table-copy"></a>Копирование удаленной таблицы
Описывает использование функции копирования удаленных таблиц для копирования таблиц из баз данных SQL Server PDW в удаленные (не устройства) SQL Server базы данных SMP. Используйте удаленную копию таблицы, чтобы включить сценарии с центральным и периферийным для SQL Server PDW.  
  
## <a name="BasicsPDE"></a>Сведения об удаленном копировании таблицы для SQL Server PDW  
Удаленная таблица Copy — это функция SQL Server PDW, которая позволяет выполнять сценарии с центральными и периферийными компонентами, копируя результаты инструкции SQL SELECT в таблицу в базе данных SMP. Копирование удаленной таблицы инициируется с помощью инструкции [CREATE Remote Table AS SELECT](../t-sql/statements/create-remote-table-as-select-parallel-data-warehouse.md) .  
  
## <a name="BasicsPrerequisites"></a>Требования для использования копирования удаленной таблицы  
Можно использовать удаленную копию таблицы для копирования таблиц из SQL Server PDW в базу данных SQL Server при соблюдении этих условий.  
  
-   Целевая база данных должна быть экземпляром Microsoft® SQL Server®, работающей в системе Microsoft Windows®, которая может подключаться к устройству SQL Server PDW, но не находится на сервере в пределах устройства. Удаленный SQL Server можно подключить к SQL Server PDWу с помощью сети InfiniBand или сети Ethernet.  
  
-   Копируемые данные должны быть выбраны с помощью одной допустимой SQL Server PDW инструкции [SELECT](../t-sql/queries/select-transact-sql.md) .  
  
-   Целевой сервер не должен быть устройством. Данные нельзя копировать непосредственно с одного устройства на другое с помощью инструкций, приведенных в этом разделе.  
  
-   Целевой сервер должен быть доступен всем узлам в сети InfiniBand устройства.  
  
## <a name="ConfigureRemote"></a>Настройка копирования удаленной таблицы  
Чтобы использовать удаленную копию таблицы, необходимо приобрести и настроить Windows Server, настроить SQL Server на Windows Server и настроить SQL Server PDW. Используйте следующие ссылки для выполнения этих трех действий по настройке.  
  
1.  [Настройка внешней системы Windows для получения копий удаленных таблиц с помощью InfiniBand](configure-an-external-windows-system-to-receive-remote-table-copies-using-infiniband.md)  
  
2.  [Настройка внешнего SQL Server SMP для получения копий удаленных таблиц](configure-an-external-smp-sql-server-to-receive-remote-table-copies.md)  
  
3.  [Настройка SQL Server PDW для удаленных копий таблиц](configure-sql-server-pdw-for-remote-table-copies.md)  
  
## <a name="PerformRemote"></a>Выполнить удаленное копирование таблицы  
Чтобы выполнить копирование удаленной таблицы, используйте инструкцию SQL [CREATE Remote Table AS SELECT](../t-sql/statements/create-remote-table-as-select-parallel-data-warehouse.md) . Примеры включены в раздел Создание удаленной таблицы.  
  
<!-- MISSING LINKS 
## See Also  
[Common Metadata Query Examples &#40;SQL Server PDW&#41;](../sqlpdw/common-metadata-query-examples-sql-server-pdw.md)  
-->
  
