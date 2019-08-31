---
title: Подключение к базе данных SQL Azure с помощью SQL Server Native Client | Документация Майкрософт
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: native-client
ms.topic: reference
ms.assetid: 0dc20bb6-b142-4259-b87b-427d2ba798af
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: f154e32b5a7782a083db73de1deef327f44e3ee2
ms.sourcegitcommit: 3b1f873f02af8f4e89facc7b25f8993f535061c9
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 08/30/2019
ms.locfileid: "70175408"
---
# <a name="connecting-to-an-azure-sql-database-using-sql-server-native-client"></a>Подключение к базе данных SQL Azure с помощью SQL Server Native Client
  Пример, демонстрирующий подключение к [!INCLUDE[ssSDSfull](../../../includes/sssdsfull-md.md)] с помощью [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] собственного клиента, см. в разделе [разработка: Разделы руководства (база данных SQL Azure)](https://msdn.microsoft.com/library/ee621787.aspx).  
  
## <a name="known-issues-when-connecting-to-a-sql-database"></a>Известные проблемы при соединении с базой данных SQL  
 Далее описаны известные проблемы при соединении с базой данных [!INCLUDE[ssSDS](../../../includes/sssds-md.md)] через [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] Native Client.  
  
-   Соединение, установленное с помощью `SQLBrowseConnect`, может быть отклонено в случае поэтапного использования `SQLBrowseConnect`.  Например, если имя драйвера передается в первом вызове, сервер и учетные данные (имя пользователя и пароль) — во втором вызове, устанавливающем соединение, а имя базы данных и язык — в третьем вызове.  После третьего вызова [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] Native Client выполняет инструкцию USE для смены базы данных. Но инструкция USE не поддерживается в службах [!INCLUDE[ssSDS](../../../includes/sssds-md.md)], и выдается следующая ошибка:  
  
    ```  
    [Microsoft][SQL Server Native Client 11.0][SQL Server]USE statement is not supported to switch between databases. Use a new connection to connect to a different Database.  
    ```  
  
## <a name="see-also"></a>См. также  
 [Построение приложений с использованием SQL Server Native Client](building-applications-with-sql-server-native-client.md)  
  
  
