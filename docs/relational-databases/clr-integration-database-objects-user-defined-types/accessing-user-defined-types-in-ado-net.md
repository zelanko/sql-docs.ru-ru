---
title: Доступ к определяемых пользователем типов в ADO.NET | Документация Майкрософт
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
manager: craigg
ms.openlocfilehash: 82ccd420318026bddac2979735c514b8b43e4a88
ms.sourcegitcommit: 61381ef939415fe019285def9450d7583df1fed0
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 10/01/2018
ms.locfileid: "47631092"
---
# <a name="accessing-user-defined-types-in-adonet"></a>Доступ к определяемым пользователем типам в ADO.NET
[!INCLUDE[appliesto-ss-xxxx-xxxx-xxx-md](../../includes/appliesto-ss-xxxx-xxxx-xxx-md.md)]
  Определяемые пользователем типы (UDT) записываются с помощью любого из языков, поддерживаемых [!INCLUDE[msCoName](../../includes/msconame-md.md)] .NET Framework CLR (CLR), создающего проверяемый код. Сюда относятся языки [!INCLUDE[msCoName](../../includes/msconame-md.md)] Visual C# и [!INCLUDE[msCoName](../../includes/msconame-md.md)] Visual Basic. Определяемые пользователем типы разрешают сохранять объекты и пользовательские структуры данных в базе данных [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]. Данные представляются как открытые элементы класса или структуры .NET Framework, а поведение определяется методами класса или структуры. Пользовательский тип можно использовать в качестве определения столбца таблицы, переменной в пакете [!INCLUDE[tsql](../../includes/tsql-md.md)], аргумента функции или хранимой процедуры [!INCLUDE[tsql](../../includes/tsql-md.md)].  
  
 В ADO.NET **System.Data.SqlClient** поставщик представляет определяемые пользователем типы следующими способами:  
  
-   Через **System.Data.SqlClient.SqlDataReader** как объект.  
  
-   Через **SqlDataReader** виде необработанных байт.  
  
-   Как параметр **System.Data.SqlClient.SqlParameter** объекта.  
  
## <a name="in-this-section"></a>в этом разделе  
 [Получение данных определяемого пользователем типа](../../relational-databases/clr-integration-database-objects-user-defined-types/accessing-user-defined-types-retrieving-udt-data.md)  
 Описывает, как получить данные определяемого пользователем типа и как указать параметры.  
  
 [Обновление столбцов определяемых пользователем типов с помощью DataAdapter](../../relational-databases/clr-integration-database-objects-user-defined-types/accessing-user-defined-types-updating-udt-columns-with-dataadapters.md)  
 Описывается работа с определяемыми пользователем типами в **наборы данных** и как обновить данные определяемого пользователем ТИПА с помощью **объектами DataAdapter**.  
  
## <a name="see-also"></a>См. также  
 [Определяемые пользователем типы в CLR](../../relational-databases/clr-integration-database-objects-user-defined-types/clr-user-defined-types.md)  
  
  
