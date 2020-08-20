---
description: Удаление SSMA для компонентов DB2 (DB2ToSQL)
title: Удаление SSMA для компонентов DB2 (DB2ToSQL) | Документация Майкрософт
ms.prod: sql
ms.custom: ''
ms.date: 01/19/2017
ms.reviewer: ''
ms.technology: ssma
ms.topic: conceptual
ms.assetid: 4ee0d698-6246-48eb-b963-d62be81cab6a
author: nahk-ivanov
ms.author: alexiva
ms.openlocfilehash: 0341869ff5d39ad35fce6ac450d293eaac1feb38
ms.sourcegitcommit: e700497f962e4c2274df16d9e651059b42ff1a10
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 08/17/2020
ms.locfileid: "88488173"
---
# <a name="removing-ssma-for-db2-components-db2tosql"></a>Удаление SSMA для компонентов DB2 (DB2ToSQL)
После завершения миграции баз данных из DB2 в [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] может потребоваться удалить компоненты SSMA. Вы можете удалить клиентские компоненты в любое время. Однако не следует удалять пакет расширений, [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] если только перенесенные базы данных больше не используют функции в схеме **ssma_DB2** базы данных **сисдб** .  
  
## <a name="uninstalling-the-ssma-for-db2-client"></a>Удаление SSMA для клиента DB2  
Удалить SSMA можно с помощью компонента " **Установка и удаление программ**".  
  
**Удаление SSMA**  
  
1.  На панели управления и откройте элемент **Установка и удаление программ**.  
  
2.  Выберите ** [!INCLUDE[msCoName](../../includes/msconame_md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Помощник по миграции для DB2**, а затем нажмите кнопку **Удалить**.  
  
3.  Чтобы подтвердить удаление SSMA, нажмите кнопку **Да**.  
  
## <a name="uninstalling-the-extension-pack"></a>Удаление пакета расширений  
Если вы уверены, что перенесенные базы данных не используют объекты в схеме **сисдб. ssma_DB2** , можно удалить пакет расширений, удалив его из схемы — нет удаления Windows  
  
## <a name="see-also"></a>См. также  
[Установка SSMA для клиента DB2 &#40;DB2ToSQL&#41;](../../ssma/db2/installing-ssma-for-db2-client-db2tosql.md)  
[Установка компонентов SSMA на SQL Server &#40;DB2ToSQL&#41;](../../ssma/db2/installing-ssma-components-on-sql-server-db2tosql.md)  
  
