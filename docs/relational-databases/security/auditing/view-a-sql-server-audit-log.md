---
title: Просмотр журнала подсистемы аудита SQL Server | Документация Майкрософт
ms.custom: ''
ms.date: 03/14/2017
ms.prod: sql
ms.prod_service: security
ms.reviewer: ''
ms.technology: security
ms.topic: conceptual
helpviewer_keywords:
- audits [SQL Server], viewing logs
- viewing audit logs
- logs [SQL Server], audit
ms.assetid: e8feaca0-7852-422b-895a-319b965d8d9b
author: VanMSFT
ms.author: vanto
ms.openlocfilehash: 9bc987034cde54d5c90392876f223ef5cf428562
ms.sourcegitcommit: b2e81cb349eecacee91cd3766410ffb3677ad7e2
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/01/2020
ms.locfileid: "72903798"
---
# <a name="view-a-sql-server-audit-log"></a>Просмотр журнала подсистемы аудита SQL Server
[!INCLUDE[appliesto-ss-xxxx-xxxx-xxx-md](../../../includes/appliesto-ss-xxxx-xxxx-xxx-md.md)]
  В этом разделе описано, как просмотреть журнал аудита SQL Server в [!INCLUDE[ssCurrent](../../../includes/sscurrent-md.md)] с помощью среды [!INCLUDE[ssManStudioFull](../../../includes/ssmanstudiofull-md.md)].  
  
 **В этом разделе**  
  
-   **Перед началом работы**  
  
     [Безопасность](#Security)  
  
-   **Просмотр журнала подсистемы аудита SQL Server с помощью:**  
  
     [Среда SQL Server Management Studio](#SSMSProcedure)  
  
##  <a name="BeforeYouBegin"></a> Перед началом  
  
###  <a name="Security"></a> безопасность  
  
####  <a name="Permissions"></a> Permissions  
 Требуется разрешение **CONTROL SERVER** .  
  
##  <a name="SSMSProcedure"></a> Использование среды SQL Server Management Studio  
  
#### <a name="to-view-a-sql-server-audit-log"></a>Просмотр журнала подсистемы аудита SQL Server  
  
1.  В обозревателе объектов раскройте папку **Безопасность** .  
  
2.  Разверните папку **Аудит** .  
  
3.  Щелкните правой кнопкой мыши журнал аудита, который необходимо просмотреть, и выберите пункт **Просмотр журналов аудита**. Открывается диалоговое окно **Просмотр файла журнала —** _имя\_сервера_. Дополнительные сведения см. в статье [Log File Viewer F1 Help](../../../relational-databases/logs/log-file-viewer-f1-help.md).  
  
4.  После завершения нажмите кнопку **Закрыть**.  

 [!INCLUDE[msCoName](../../../includes/msconame-md.md)] рекомендует просматривать журнал аудита, используя средство просмотра файлов журнала. Однако при создании автоматизированной системы мониторинга информацию в файле аудита можно просматривать напрямую с помощью функции [sys.fn_get_audit_file (Transact-SQL)](../../../relational-databases/system-functions/sys-fn-get-audit-file-transact-sql.md). При чтении файла напрямую данные возвращаются в несколько ином (необработанном) формате. Дополнительные сведения см. в статье **sys.fn_get_audit_file** .  
  
## <a name="see-also"></a>См. также:  
 [Подсистема аудита SQL Server (компонент Database Engine)](../../../relational-databases/security/auditing/sql-server-audit-database-engine.md)   
 [Запись событий подсистемы аудита SQL Server в журнал безопасности](../../../relational-databases/security/auditing/write-sql-server-audit-events-to-the-security-log.md)  
  
  
