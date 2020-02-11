---
title: Удаление SSMA для компонентов DB2 (DB2ToSQL) | Документация Майкрософт
ms.prod: sql
ms.custom: ''
ms.date: 01/19/2017
ms.reviewer: ''
ms.technology: ssma
ms.topic: conceptual
ms.assetid: 4ee0d698-6246-48eb-b963-d62be81cab6a
author: Shamikg
ms.author: Shamikg
ms.openlocfilehash: 25c8222009c2ea9358c0bab2ad5ae077588fb3cb
ms.sourcegitcommit: b87d36c46b39af8b929ad94ec707dee8800950f5
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/08/2020
ms.locfileid: "68060099"
---
# <a name="removing-ssma-for-db2-components-db2tosql"></a>Удаление SSMA для компонентов DB2 (DB2ToSQL)
После завершения миграции баз данных из DB2 в [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]может потребоваться удалить компоненты SSMA. Вы можете удалить клиентские компоненты в любое время. Однако не следует удалять пакет расширений, [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] если только перенесенные базы данных больше не используют функции в схеме **ssma_DB2** базы данных **сисдб** .  
  
## <a name="uninstalling-the-ssma-for-db2-client"></a>Удаление SSMA для клиента DB2  
Удалить SSMA можно с помощью компонента " **Установка и удаление программ**".  
  
**Удаление SSMA**  
  
1.  На панели управления и откройте элемент **Установка и удаление программ**.  
  
2.  ** [!INCLUDE[msCoName](../../includes/msconame_md.md)] Выберите [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] помощник по миграции для DB2**, а затем нажмите кнопку **Удалить**.  
  
3.  Чтобы подтвердить удаление SSMA, нажмите кнопку **Да**.  
  
## <a name="uninstalling-the-extension-pack"></a>Удаление пакета расширений  
Если вы уверены, что перенесенные базы данных не используют объекты в схеме **сисдб. ssma_DB2** , можно удалить пакет расширений, удалив его из схемы — нет удаления Windows  
  
## <a name="see-also"></a>См. также:  
[Установка SSMA для клиента DB2 &#40;DB2ToSQL&#41;](../../ssma/db2/installing-ssma-for-db2-client-db2tosql.md)  
[Установка компонентов SSMA на SQL Server &#40;DB2ToSQL&#41;](../../ssma/db2/installing-ssma-components-on-sql-server-db2tosql.md)  
  
