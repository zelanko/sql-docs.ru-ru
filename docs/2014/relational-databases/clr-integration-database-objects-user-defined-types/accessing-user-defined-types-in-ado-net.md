---
title: Доступ к определяемым пользователем типам в ADO.NET | Документация Майкрософт
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
ms.openlocfilehash: a94e333ad743ed07dff6b973ebfe227312a1cab2
ms.sourcegitcommit: f71e523da72019de81a8bd5a0394a62f7f76ea20
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 06/17/2020
ms.locfileid: "84970764"
---
# <a name="accessing-user-defined-types-in-adonet"></a>Доступ к определяемым пользователем типам в ADO.NET
  Определяемые пользователем типы записываются с помощью любого языка, поддерживаемого [!INCLUDE[msCoName](../../includes/msconame-md.md)] .NET Framework среде CLR, которая создает проверяемый код. Сюда относятся языки [!INCLUDE[msCoName](../../includes/msconame-md.md)] Visual C# и [!INCLUDE[msCoName](../../includes/msconame-md.md)] Visual Basic. Определяемые пользователем типы разрешают сохранять объекты и пользовательские структуры данных в базе данных [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]. Данные представляются как открытые элементы класса или структуры .NET Framework, а поведение определяется методами класса или структуры. Пользовательский тип можно использовать в качестве определения столбца таблицы, переменной в пакете [!INCLUDE[tsql](../../includes/tsql-md.md)], аргумента функции или хранимой процедуры [!INCLUDE[tsql](../../includes/tsql-md.md)].  
  
 В ADO.NET поставщик `System.Data.SqlClient` представляет определяемые пользователем типы следующими способами.  
  
-   Через класс `System.Data.SqlClient.SqlDataReader` в виде объекта.  
  
-   Через объект `SqlDataReader` в виде необработанных байт.  
  
-   В виде параметра объекта `System.Data.SqlClient.SqlParameter`.  
  
## <a name="in-this-section"></a>В этом разделе  
 [Получение данных определяемого пользователем типа](accessing-user-defined-types-retrieving-udt-data.md)  
 Описывает, как получить данные определяемого пользователем типа и как указать параметры.  
  
 [Обновление столбцов определяемых пользователем типов с помощью DataAdapter](accessing-user-defined-types-updating-udt-columns-with-dataadapters.md)  
 Описывает, как работать с определяемыми пользователем типами в `DataSets` и как обновить данные определяемого пользователем типа с помощью `DataAdapters`.  
  
## <a name="see-also"></a>См. также:  
 [Определяемые пользователем типы данных CLR](clr-user-defined-types.md)  
  
  
