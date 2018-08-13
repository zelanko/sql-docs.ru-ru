---
title: Подключение к базе данных Azure SQL Windows, с помощью собственного клиента SQL Server | Документация Майкрософт
ms.custom: ''
ms.date: 03/14/2017
ms.reviewer: ''
ms.suite: sql
ms.prod: sql
ms.technology: native-client
ms.tgt_pltfrm: ''
ms.topic: reference
ms.assetid: 0dc20bb6-b142-4259-b87b-427d2ba798af
caps.latest.revision: 6
author: MightyPen
ms.author: genemi
manager: craigg
monikerRange: '>=aps-pdw-2016||=azuresqldb-current||=azure-sqldw-latest||>=sql-server-2016||=sqlallproducts-allversions||>=sql-server-linux-2017'
ms.openlocfilehash: 3ed7b020e923406aa88b7296da3732d728c8d9d9
ms.sourcegitcommit: 4cd008a77f456b35204989bbdd31db352716bbe6
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 08/06/2018
ms.locfileid: "39561084"
---
# <a name="connecting-to-a-windows-azure-sql-database-using-sql-server-native-client"></a>Соединение с базой данных SQL Windows Azure с помощью SQL Server Native Client
[!INCLUDE[appliesto-ss-asdb-asdw-pdw-md](../../../includes/appliesto-ss-asdb-asdw-pdw-md.md)]
[!INCLUDE[SNAC_Deprecated](../../../includes/snac-deprecated.md)]

  Пример, в котором показано, как подключиться к [!INCLUDE[ssSDSfull](../../../includes/sssdsfull-md.md)] с помощью [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] Native Client, см. в разделе [разработки: инструкции (база данных SQL Azure Windows)](http://msdn.microsoft.com/library/ee621787.aspx).  
  
## <a name="known-issues-when-connecting-to-a-sql-database"></a>Известные проблемы при соединении с базой данных SQL  
 Далее описаны известные проблемы при соединении с базой данных [!INCLUDE[ssSDS](../../../includes/sssds-md.md)] через [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] Native Client.  
  
-   Подключение с **SQLBrowseConnect** может быть отклонен, если **SQLBrowseConnect** используется поэтапно.  Например, если имя драйвера передается в первом вызове, сервер и учетные данные (имя пользователя и пароль) — во втором вызове, устанавливающем соединение, а имя базы данных и язык — в третьем вызове.  После третьего вызова [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] Native Client выполняет инструкцию USE для смены базы данных. Но инструкция USE не поддерживается в службах [!INCLUDE[ssSDS](../../../includes/sssds-md.md)], и выдается следующая ошибка:  
  
    ```  
    [Microsoft][SQL Server Native Client 11.0][SQL Server]USE statement is not supported to switch between databases. Use a new connection to connect to a different Database.  
    ```  
  
## <a name="see-also"></a>См. также  
 [Построение приложений с использованием SQL Server Native Client](../../../relational-databases/native-client/applications/building-applications-with-sql-server-native-client.md)  
  
  
