---
title: Поддержка UTF-16
description: Узнайте о поддержке UTF-16 в буфере фиксированной длины в SQL Server Native Client, начиная с SQL Server 2012.
ms.custom: ''
ms.date: 03/14/2017
ms.prod: sql
ms.reviewer: ''
ms.technology: native-client
ms.topic: reference
ms.assetid: f2520424-8ef4-409f-8147-d83da5076e96
author: markingmyname
ms.author: maghan
monikerRange: '>=aps-pdw-2016||=azuresqldb-current||=azure-sqldw-latest||>=sql-server-2016||=sqlallproducts-allversions||>=sql-server-linux-2017||=azuresqldb-mi-current'
ms.openlocfilehash: 9b538c19ebb1c0841ffb4da5ec403f5986d626e2
ms.sourcegitcommit: da88320c474c1c9124574f90d549c50ee3387b4c
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 07/01/2020
ms.locfileid: "85719624"
---
# <a name="utf-16-support-in-sql-server-native-client-110"></a>Поддержка UTF-16 в собственном клиенте SQL Server версии 11.0
[!INCLUDE [SQL Server](../../../includes/applies-to-version/sql-asdb-asdbmi-asdw-pdw.md)]

  Начиная с [!INCLUDE[ssSQL11](../../../includes/sssql11-md.md)], если при привязке результата столбца или выходного параметра указывается буфер фиксированной длины, а символ **wchar** , записываемый в буфер перед завершающим символом, является старшим символом суррогатной пары, а следующий символ **wchar** является младшим символом суррогатной пары, то собственный клиент [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] не добавит в буфер старший символ суррогатной пары.  
  
## <a name="see-also"></a>См. также  
 [Компоненты собственного клиента SQL Server](../../../relational-databases/native-client/features/sql-server-native-client-features.md)  
  
  
