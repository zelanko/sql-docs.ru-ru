---
title: Удаление SSMA для DB2 компонентов (DB2ToSQL) | Документы Microsoft
ms.prod: sql
ms.custom: ''
ms.date: 01/19/2017
ms.reviewer: ''
ms.suite: sql
ms.technology: ssma
ms.tgt_pltfrm: ''
ms.topic: conceptual
applies_to:
- Azure SQL Database
- SQL Server
ms.assetid: 4ee0d698-6246-48eb-b963-d62be81cab6a
caps.latest.revision: 6
author: Shamikg
ms.author: Shamikg
manager: craigg
ms.openlocfilehash: 330ce4dee20972148ff74d85e892d879e8b5203a
ms.sourcegitcommit: 8aa151e3280eb6372bf95fab63ecbab9dd3f2e5e
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 06/05/2018
ms.locfileid: "34775370"
---
# <a name="removing-ssma-for-db2-components-db2tosql"></a>Удаление SSMA для DB2 компонентов (DB2ToSQL)
После завершения миграции баз данных DB2 и [!INCLUDE[ssNoVersion](../../includes/ssnoversion_md.md)], может потребоваться удалить компоненты SSMA. Клиентские компоненты можно удалить в любое время. Однако не рекомендуется удалять пакет расширения из [!INCLUDE[ssNoVersion](../../includes/ssnoversion_md.md)] Если перенесенной базы данных больше не использовать функции в **ssma_DB2** схему **sysdb** базы данных.  
  
## <a name="uninstalling-the-ssma-for-db2-client"></a>При удалении SSMA для DB2 клиента  
SSMA можно удалить с помощью **Установка и удаление программ**.  
  
**Чтобы удалить SSMA**  
  
1.  В панели управления откройте **Установка и удаление программ**.  
  
2.  Выберите  **[!INCLUDE[msCoName](../../includes/msconame_md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion_md.md)] помощник по миграции для DB2**, а затем нажмите кнопку **удалить**.  
  
3.  Чтобы подтвердить, что вы хотите удалить SSMA, щелкните **Да**.  
  
## <a name="uninstalling-the-extension-pack"></a>Удаление пакета расширения  
Если вы уверены, перенесенных баз данных не следует использовать объекты в **sysdb.ssma_DB2** схемы, пакет расширение можно удалить, удалив его из схемы — существует является удаление Windows  
  
## <a name="see-also"></a>См. также  
[Установка SSMA для клиента DB2 &#40;DB2ToSQL&#41;](../../ssma/db2/installing-ssma-for-db2-client-db2tosql.md)  
[Установка компонентов SSMA на SQL Server &#40;DB2ToSQL&#41;](../../ssma/db2/installing-ssma-components-on-sql-server-db2tosql.md)  
  
