---
title: Доступ к определенным типам пользователей в ADO.NET Документы Майкрософт
description: UDT, написанные на языках .NET Framework CLR, позволяют базе данных S'L Server хранить объекты и пользовательские структуры данных. В ADO.NET поставщик предоставляет UDT.
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
ms.sourcegitcommit: b2cc3f213042813af803ced37901c5c9d8016c24
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/16/2020
ms.locfileid: "81488265"
---
# <a name="accessing-user-defined-types-in-adonet"></a>Доступ к определяемым пользователем типам в ADO.NET
[!INCLUDE[appliesto-ss-xxxx-xxxx-xxx-md](../../includes/appliesto-ss-xxxx-xxxx-xxx-md.md)]
  Типы, определяемые пользователями (UDT), [!INCLUDE[msCoName](../../includes/msconame-md.md)] пишутся с использованием любого из языков, поддерживаемых общим временем выполнения языка .NET Framework (CLR), которые производят проверяемый код. Сюда относятся языки [!INCLUDE[msCoName](../../includes/msconame-md.md)] Visual C# и [!INCLUDE[msCoName](../../includes/msconame-md.md)] Visual Basic. Определяемые пользователем типы разрешают сохранять объекты и пользовательские структуры данных в базе данных [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]. Данные представляются как открытые элементы класса или структуры .NET Framework, а поведение определяется методами класса или структуры. Пользовательский тип можно использовать в качестве определения столбца таблицы, переменной в пакете [!INCLUDE[tsql](../../includes/tsql-md.md)], аргумента функции или хранимой процедуры [!INCLUDE[tsql](../../includes/tsql-md.md)].  
  
 В ADO.NET провайдер **System.Data.SqlClient** предоставляет UDT следующим образом:  
  
-   Через **System.Data.SqlClient.SqlDataReader** как объект.  
  
-   Через **SqlDataReader** в качестве сырых байтов.  
  
-   В качестве параметра объекта **System.Data.SqlClient.SqlParameter.**  
  
## <a name="in-this-section"></a>В этом разделе  
 [Получение данных определяемого пользователем типа](../../relational-databases/clr-integration-database-objects-user-defined-types/accessing-user-defined-types-retrieving-udt-data.md)  
 Описывает, как получить данные определяемого пользователем типа и как указать параметры.  
  
 [Обновление столбцов определяемых пользователем типов с помощью DataAdapter](../../relational-databases/clr-integration-database-objects-user-defined-types/accessing-user-defined-types-updating-udt-columns-with-dataadapters.md)  
 Описывает, как работать с UDT в **DataSets** и как обновлять данные UDT с помощью **DataAdapters.**  
  
## <a name="see-also"></a>См. также:  
 [Определяемые пользователем типы данных CLR](../../relational-databases/clr-integration-database-objects-user-defined-types/clr-user-defined-types.md)  
  
  
