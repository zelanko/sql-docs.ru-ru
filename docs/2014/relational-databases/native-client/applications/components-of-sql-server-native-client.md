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
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: 329ffa78471ead02b1431a41d898cfc43ca65684
ms.sourcegitcommit: 3026c22b7fba19059a769ea5f367c4f51efaf286
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 06/15/2019
ms.locfileid: "63213516"
---
# <a name="components-of-sql-server-native-client"></a>Компоненты собственного клиента SQL Server
  [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] Native Client содержит следующие компоненты.  
  
|Компонент|Описание|  
|---------------|-----------------|  
|sqlncli11.dll|Файл динамически подключаемой библиотеки (DLL), включающий все функциональные возможности [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] Native Client. В его состав входят поставщик OLE DB [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] Native Client и драйвер ODBC [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] Native Client.|  
|sqlnclir11.rll|Соответствующий файл ресурса для библиотеки [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] Native Client.|  
|s10ch_sqlncli.chm|Файл справки мастера источников данных, описывающий, как создавать источник данных [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)], использовать драйвер ODBC собственного клиента [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] или поставщик OLE DB собственного клиента [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)].|  
|sqlncli.h|Файл заголовка собственного клиента [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)], который содержит все определения, необходимые для использования собственного клиента [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)]. Этот файл заголовка заменяет оба файла заголовков — odbcss.h и the sqloledb.h. **Примечание.**  Нельзя сослаться на sqlncli.h и odbcss.h в одной программе, но можно ссылаться на файл sqlncli.h и sqloledb.h в одной программе до тех пор, пока что sqloledb.h указывается первым.|  
|sqlncli11.lib|Файл библиотеки, необходимый для прямого вызова **bcp** служебных функций, которые являются частью [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] драйвер ODBC собственного клиента. **Примечание.**  Если в программном коде есть ссылка на файл sqlncli11.lib, необходимо убедиться, что файл sqlncli11.dll находится в вашем системном пути и в системных путях пользователей, использовать приложения.|  
  
## <a name="see-also"></a>См. также  
 [Построение приложений с использованием SQL Server Native Client](building-applications-with-sql-server-native-client.md)  
  
  
