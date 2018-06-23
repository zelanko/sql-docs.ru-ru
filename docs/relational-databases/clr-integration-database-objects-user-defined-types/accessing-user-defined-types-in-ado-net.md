---
title: Доступ к определяемых пользователем типов в ADO.NET | Документы Microsoft
ms.custom: ''
ms.date: 03/14/2017
ms.prod: sql
ms.reviewer: ''
ms.suite: sql
ms.technology: reference
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
ms.openlocfilehash: f9df05bab46774ebd9e033c47565294ee9c46857
ms.sourcegitcommit: a78fa85609a82e905de9db8b75d2e83257831ad9
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 06/18/2018
ms.locfileid: "35696735"
---
# <a name="accessing-user-defined-types-in-adonet"></a>Доступ к определяемым пользователем типам в ADO.NET
[!INCLUDE[appliesto-ss-xxxx-xxxx-xxx-md](../../includes/appliesto-ss-xxxx-xxxx-xxx-md.md)]
  Определяемые пользователем типы (UDT) пишутся на любом из языков, поддерживаемых [!INCLUDE[msCoName](../../includes/msconame-md.md)] .NET Framework CLR (CLR), создающего проверяемый код. Сюда относятся языки [!INCLUDE[msCoName](../../includes/msconame-md.md)] Visual C# и [!INCLUDE[msCoName](../../includes/msconame-md.md)] Visual Basic. Определяемые пользователем типы разрешают сохранять объекты и пользовательские структуры данных в базе данных [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]. Данные представляются как открытые элементы класса или структуры .NET Framework, а поведение определяется методами класса или структуры. Определяемый пользователем тип можно использовать в качестве определения столбца таблицы, в переменной [!INCLUDE[tsql](../../includes/tsql-md.md)] пакет, или как аргумент [!INCLUDE[tsql](../../includes/tsql-md.md)] функции или хранимой процедуры.  
  
 В ADO.NET **System.Data.SqlClient** поставщик представляет определяемые пользователем типы следующими способами:  
  
-   Через **System.Data.SqlClient.SqlDataReader** как объект.  
  
-   Через **SqlDataReader** как необработанные байты.  
  
-   Как параметр **System.Data.SqlClient.SqlParameter** объекта.  
  
## <a name="in-this-section"></a>в этом разделе  
 [Получение данных определяемого пользователем типа](../../relational-databases/clr-integration-database-objects-user-defined-types/accessing-user-defined-types-retrieving-udt-data.md)  
 Описывает, как получить данные определяемого пользователем типа и как указать параметры.  
  
 [Обновление столбцов определяемых пользователем типов с помощью DataAdapter](../../relational-databases/clr-integration-database-objects-user-defined-types/accessing-user-defined-types-updating-udt-columns-with-dataadapters.md)  
 Описывает способы работы с определяемыми пользователем типами в **наборы данных** и как обновить определяемого пользователем ТИПА данных, с помощью **адаптеров данных**.  
  
## <a name="see-also"></a>См. также  
 [Определяемые пользователем типы в CLR](../../relational-databases/clr-integration-database-objects-user-defined-types/clr-user-defined-types.md)  
  
  
