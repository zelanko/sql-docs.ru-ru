---
title: Удаление SSMA для DB2 компонентов (DB2ToSQL) | Документация Майкрософт
ms.prod: sql
ms.custom: ''
ms.date: 01/19/2017
ms.reviewer: ''
ms.technology: ssma
ms.topic: conceptual
ms.assetid: 4ee0d698-6246-48eb-b963-d62be81cab6a
author: Shamikg
ms.author: Shamikg
manager: craigg
ms.openlocfilehash: d4f819a92885cf5d173bcdda53ebf3291c958eac
ms.sourcegitcommit: 3026c22b7fba19059a769ea5f367c4f51efaf286
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 06/15/2019
ms.locfileid: "63270109"
---
# <a name="removing-ssma-for-db2-components-db2tosql"></a>Удаление SSMA для DB2 компонентов (DB2ToSQL)
После завершения миграции баз данных из DB2 в [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)], может потребоваться удаление компонентов SSMA. Клиентские компоненты можно удалить в любое время. Тем не менее, не рекомендуется удалять пакет расширений из [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] перенесенных баз данных больше не использовать функции в **ssma_DB2** схему **sysdb** базы данных.  
  
## <a name="uninstalling-the-ssma-for-db2-client"></a>Удаление SSMA для DB2 клиента  
SSMA можно удалить с помощью **Установка и удаление программ**.  
  
**Чтобы удалить SSMA**  
  
1.  В панели управления откройте **Установка и удаление программ**.  
  
2.  Выберите  **[!INCLUDE[msCoName](../../includes/msconame_md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] помощника по миграции для DB2**, а затем нажмите кнопку **удалить**.  
  
3.  Чтобы убедиться, что вы хотите удалить SSMA, щелкните **Да**.  
  
## <a name="uninstalling-the-extension-pack"></a>Удаление пакета расширения  
Если вы уверены, перенесенных баз данных не следует использовать объекты в **sysdb.ssma_DB2** схемы, можно удалить пакет расширений, удалив его из схемы — имеется еще удаление не Windows  
  
## <a name="see-also"></a>См. также  
[Установка SSMA для DB2 клиента &#40;DB2ToSQL&#41;](../../ssma/db2/installing-ssma-for-db2-client-db2tosql.md)  
[Установка компонентов SSMA в SQL Server &#40;DB2ToSQL&#41;](../../ssma/db2/installing-ssma-components-on-sql-server-db2tosql.md)  
  
