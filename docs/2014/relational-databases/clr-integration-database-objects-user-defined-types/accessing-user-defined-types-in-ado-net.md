---
title: Доступ к определяемых пользователем типов в ADO.NET | Документация Майкрософт
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: clr
ms.topic: reference
helpviewer_keywords:
- ADO.NET [CLR integration]
- UDTs [CLR integration], ADO.NET
- user-defined types [CLR integration], ADO.NET
ms.assetid: 4b0d876c-8066-490e-8e18-327c0e942b19
author: rothja
ms.author: jroth
manager: craigg
ms.openlocfilehash: 893b2c69a20974bb379cc032f442e5fcb3525ec5
ms.sourcegitcommit: 3026c22b7fba19059a769ea5f367c4f51efaf286
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 06/15/2019
ms.locfileid: "62919684"
---
# <a name="accessing-user-defined-types-in-adonet"></a>Доступ к определяемым пользователем типам в ADO.NET
  Определяемые пользователем типы (UDT) записываются с помощью любого из языков, поддерживаемых [!INCLUDE[msCoName](../../includes/msconame-md.md)] .NET Framework CLR (CLR), создающего проверяемый код. Сюда относятся языки [!INCLUDE[msCoName](../../includes/msconame-md.md)] Visual C# и [!INCLUDE[msCoName](../../includes/msconame-md.md)] Visual Basic. Определяемые пользователем типы разрешают сохранять объекты и пользовательские структуры данных в базе данных [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]. Данные представляются как открытые элементы класса или структуры .NET Framework, а поведение определяется методами класса или структуры. Пользовательский тип можно использовать в качестве определения столбца таблицы, переменной в пакете [!INCLUDE[tsql](../../includes/tsql-md.md)], аргумента функции или хранимой процедуры [!INCLUDE[tsql](../../includes/tsql-md.md)].  
  
 В ADO.NET поставщик `System.Data.SqlClient` представляет определяемые пользователем типы следующими способами.  
  
-   Через класс `System.Data.SqlClient.SqlDataReader` в виде объекта.  
  
-   Через объект `SqlDataReader` в виде необработанных байт.  
  
-   В виде параметра объекта `System.Data.SqlClient.SqlParameter`.  
  
## <a name="in-this-section"></a>в этом разделе  
 [Получение данных определяемого пользователем типа](accessing-user-defined-types-retrieving-udt-data.md)  
 Описывает, как получить данные определяемого пользователем типа и как указать параметры.  
  
 [Обновление столбцов определяемых пользователем типов с помощью DataAdapter](accessing-user-defined-types-updating-udt-columns-with-dataadapters.md)  
 Описывает, как работать с определяемыми пользователем типами в `DataSets` и как обновить данные определяемого пользователем типа с помощью `DataAdapters`.  
  
## <a name="see-also"></a>См. также  
 [Определяемые пользователем типы в CLR](clr-user-defined-types.md)  
  
  
