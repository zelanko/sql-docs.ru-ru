---
title: Настройка свойств сборщика данных | Документация Майкрософт
ms.custom: ''
ms.date: 03/01/2017
ms.prod: sql
ms.reviewer: ''
ms.technology: supportability
ms.topic: conceptual
f1_keywords:
- sql13.swb.dc.datacollectionprop.general.f1
- sql13.swb.dc.datacollectionprop.advanced.f1
ms.assetid: cf98f57d-5a6d-4bc3-bf10-783e460fc63d
author: MashaMSFT
ms.author: mathoma
manager: craigg
ms.openlocfilehash: 67df1557cf4035f4e7bfca1eaa23d9bb0505c8e1
ms.sourcegitcommit: 61381ef939415fe019285def9450d7583df1fed0
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 10/01/2018
ms.locfileid: "47757982"
---
# <a name="configure-properties-of-a-data-collector"></a>Настройка свойств сборщика данных
[!INCLUDE[appliesto-ss-xxxx-xxxx-xxx-md](../../includes/appliesto-ss-xxxx-xxxx-xxx-md.md)]
  В этом разделе рассматривается настройка свойств сборщика данных.  
  
## <a name="data-collection-properties-general-tab"></a>Свойства сбора данных (вкладка «Общие»)  
 Эта страница используется для настройки параметров хранилища данных управления и указания места хранения собранных данных перед передачей в хранилище данных.  
  
 **Включить сбор данных**  
 Выберите, чтобы включить сбор данных. Результат этого действия такой же, как при запуске хранимой процедуры sp_syscollector_enable_collector. При снятии флажка сбор данных отключается, результат такой же, как при запуске хранимой процедуры sp_syscollector_disable_collector.  
  
 **Server**  
 Отображает имя сервера, на котором будет размещено хранилище данных управления.  
  
 **Имя базы данных**  
 Отображает имя реляционной базы данных, которая используется для хранилища управляющих данных.  
  
 **Проверка соединения**  
 Проверяет соединение с указанным **Сервером** с использованием данных, предоставленных при настройке сборщика данных.  
  
 **Каталог кэша**  
 Указывает каталог, в котором хранятся собранные данные на локальном компьютере до их передачи в хранилище управляющих данных. Если **Каталог кэша** не указан, сборщик данных предпринимает попытку обнаружить переменные среды %TEMP% и %TMP% и использует одно из этих мест в качестве временного хранилища по умолчанию. Если эти переменные среды не заданы, выдается ошибка и запрос для создания каталога кэша.  
  
## <a name="data-collection-properties-advanced-tab"></a>Свойства сбора данных (вкладка «Дополнительно»)  
 Эта страница используется для настройки параметров повторных попыток соединения с хранилищем данных управления.  
  
 **Количество повторных попыток в случае ошибки передачи**  
 Указывает число повторных попыток передачи в хранилище управляющих данных, если передача завершается ошибкой. Значение по умолчанию равно 1.  
  
## <a name="see-also"></a>См. также:  
 [Управление сбором данных](../../relational-databases/data-collection/manage-data-collection.md)   
 [Настройка хранилища данных управления (среда SQL Server Management Studio)](../../relational-databases/data-collection/configure-the-management-data-warehouse-sql-server-management-studio.md)  
  
  
