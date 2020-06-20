---
title: Компоненты SQL Server Native Client | Документация Майкрософт
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: native-client
ms.topic: reference
helpviewer_keywords:
- SQL Server Native Client ODBC driver, about SQL Server Native Client ODBC driver
- data access [SQL Server Native Client], components
- components [SQL Server Native Client]
- SQLNCLI, about SQL Server Native Client
ms.assetid: 65f932d5-daa1-4eff-b6df-ee633fcf2a7c
author: rothja
ms.author: jroth
ms.openlocfilehash: 32438b9fb5473d9251acd0aceddb46db373f3548
ms.sourcegitcommit: 57f1d15c67113bbadd40861b886d6929aacd3467
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 06/18/2020
ms.locfileid: "85017650"
---
# <a name="components-of-sql-server-native-client"></a>Компоненты собственного клиента SQL Server
  [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] Native Client содержит следующие компоненты.  
  
|Компонент|Описание|  
|---------------|-----------------|  
|sqlncli11.dll|Файл динамически подключаемой библиотеки (DLL), включающий все функциональные возможности [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] Native Client. В его состав входят поставщик OLE DB [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] Native Client и драйвер ODBC [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] Native Client.|  
|sqlnclir11.rll|Соответствующий файл ресурса для библиотеки [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] Native Client.|  
|s10ch_sqlncli.chm|Файл справки мастера источников данных, описывающий, как создавать источник данных [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)], использовать драйвер ODBC собственного клиента [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] или поставщик OLE DB собственного клиента [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)].|  
|sqlncli.h|Файл заголовка собственного клиента [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)], который содержит все определения, необходимые для использования собственного клиента [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)]. Этот файл заголовка заменяет оба файла заголовков — odbcss.h и the sqloledb.h. **Примечание.**  В той же программе нельзя ссылаться на SQLNCLI. h и ODBC. h, но можно ссылаться на SQLNCLI. h и SQLOLEDB. h в той же программе, если только SQLOLEDB. h определен первым.|  
|sqlncli11.lib|Файл библиотеки, необходимый для непосредственного вызова функций программы **bcp** , которые являются частью [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] драйвера ODBC для собственного клиента. **Примечание.**  Если вы ссылаетесь на файл sqlncli11. lib в программном коде, необходимо убедиться, что файл sqlncli11.dll находится в системном пути, и в системном пути пользователей, которые используют ваше приложение.|  
  
## <a name="see-also"></a>См. также:  
 [Построение приложений с использованием SQL Server Native Client](building-applications-with-sql-server-native-client.md)  
  
  
