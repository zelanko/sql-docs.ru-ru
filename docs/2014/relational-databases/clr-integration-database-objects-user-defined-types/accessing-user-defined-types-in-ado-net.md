---
title: Доступ к определяемых пользователем типов в ADO.NET | Документация Майкрософт
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.suite: ''
ms.technology: clr
ms.tgt_pltfrm: ''
ms.topic: reference
helpviewer_keywords:
- ADO.NET [CLR integration]
- UDTs [CLR integration], ADO.NET
- user-defined types [CLR integration], ADO.NET
ms.assetid: 4b0d876c-8066-490e-8e18-327c0e942b19
caps.latest.revision: 12
author: rothja
ms.author: jroth
manager: craigg
ms.openlocfilehash: 6b48d45874824f166dc1b3843eda0e1052fddfd6
ms.sourcegitcommit: 022d67cfbc4fdadaa65b499aa7a6a8a942bc502d
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 07/03/2018
ms.locfileid: "37354666"
---
# <a name="accessing-user-defined-types-in-adonet"></a>Доступ к определяемым пользователем типам в ADO.NET
  Определяемые пользователем типы (UDT) записываются с помощью любого из языков, поддерживаемых [!INCLUDE[msCoName](../../includes/msconame-md.md)] .NET Framework CLR (CLR), создающего проверяемый код. Сюда относятся языки [!INCLUDE[msCoName](../../includes/msconame-md.md)] Visual C# и [!INCLUDE[msCoName](../../includes/msconame-md.md)] Visual Basic. Определяемые пользователем типы разрешают сохранять объекты и пользовательские структуры данных в базе данных [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]. Данные представляются как открытые элементы класса или структуры .NET Framework, а поведение определяется методами класса или структуры. Определяемый пользователем тип можно использовать в качестве определения столбца таблицы, в качестве переменной [!INCLUDE[tsql](../../includes/tsql-md.md)] пакетной службы, или в качестве аргумента [!INCLUDE[tsql](../../includes/tsql-md.md)] функции или хранимой процедуры.  
  
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
  
  
