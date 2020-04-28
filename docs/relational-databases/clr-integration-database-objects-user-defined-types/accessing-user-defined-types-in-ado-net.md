---
title: Доступ к определяемым пользователем типам в ADO.NET | Документация Майкрософт
description: Определяемые пользователем типы, написанные на языках .NET Framework CLR, позволяют базе данных SQL Server хранить объекты и пользовательские структуры данных. В ADO.NET поставщик предоставляет определяемые пользователем типы.
ms.custom: ''
ms.date: 03/14/2017
ms.prod: sql
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
ms.openlocfilehash: d14205a6fb506f5d4fddaac1ab601ff1ee9205b8
ms.sourcegitcommit: e042272a38fb646df05152c676e5cbeae3f9cd13
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/27/2020
ms.locfileid: "81488265"
---
# <a name="accessing-user-defined-types-in-adonet"></a>Доступ к определяемым пользователем типам в ADO.NET
[!INCLUDE[appliesto-ss-xxxx-xxxx-xxx-md](../../includes/appliesto-ss-xxxx-xxxx-xxx-md.md)]
  Определяемые пользователем типы записываются с помощью любого языка, поддерживаемого [!INCLUDE[msCoName](../../includes/msconame-md.md)] .NET Framework среде CLR, которая создает проверяемый код. Сюда относятся языки [!INCLUDE[msCoName](../../includes/msconame-md.md)] Visual C# и [!INCLUDE[msCoName](../../includes/msconame-md.md)] Visual Basic. Определяемые пользователем типы разрешают сохранять объекты и пользовательские структуры данных в базе данных [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]. Данные представляются как открытые элементы класса или структуры .NET Framework, а поведение определяется методами класса или структуры. Пользовательский тип можно использовать в качестве определения столбца таблицы, переменной в пакете [!INCLUDE[tsql](../../includes/tsql-md.md)], аргумента функции или хранимой процедуры [!INCLUDE[tsql](../../includes/tsql-md.md)].  
  
 В ADO.NET поставщик **System. Data. SqlClient** предоставляет определяемые пользователем типы следующими способами:  
  
-   Через **System. Data. SqlClient. SqlDataReader** в качестве объекта.  
  
-   Через **SqlDataReader** как необработанные байты.  
  
-   В качестве параметра объекта **System. Data. SqlClient. SqlParameter** .  
  
## <a name="in-this-section"></a>В этом разделе  
 [Получение данных определяемого пользователем типа](../../relational-databases/clr-integration-database-objects-user-defined-types/accessing-user-defined-types-retrieving-udt-data.md)  
 Описывает, как получить данные определяемого пользователем типа и как указать параметры.  
  
 [Обновление столбцов определяемых пользователем типов с помощью DataAdapter](../../relational-databases/clr-integration-database-objects-user-defined-types/accessing-user-defined-types-updating-udt-columns-with-dataadapters.md)  
 Описывает, как работать с определяемыми пользователем типами в **наборах** данных и как обновлять данные определяемых пользователем типов с помощью **DataAdapter**.  
  
## <a name="see-also"></a>См. также:  
 [Определяемые пользователем типы данных CLR](../../relational-databases/clr-integration-database-objects-user-defined-types/clr-user-defined-types.md)  
  
  
