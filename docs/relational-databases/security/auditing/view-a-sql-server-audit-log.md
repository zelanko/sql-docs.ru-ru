---
title: "Просмотр журнала подсистемы аудита SQL Server | Microsoft Docs"
ms.custom: ""
ms.date: "03/14/2017"
ms.prod: "sql-server-2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "database-engine"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "аудиты [SQL Server], просмотр журналов"
  - "просмотр журналов аудита"
  - "журналы [SQL Server], аудит"
ms.assetid: e8feaca0-7852-422b-895a-319b965d8d9b
caps.latest.revision: 12
author: "BYHAM"
ms.author: "rickbyh"
manager: "jhubbard"
caps.handback.revision: 12
---
# Просмотр журнала подсистемы аудита SQL Server
  В этом разделе описано, как просмотреть журнал аудита SQL Server в [!INCLUDE[ssCurrent](../../../includes/sscurrent-md.md)] с помощью среды [!INCLUDE[ssManStudioFull](../../../includes/ssmanstudiofull-md.md)].  
  
 **В этом разделе**  
  
-   **Перед началом работы выполните следующие действия.**  
  
     [Безопасность](#Security)  
  
-   **Просмотр журнала подсистемы аудита SQL Server с помощью:**  
  
     [Среда SQL Server Management Studio](#SSMSProcedure)  
  
##  <a name="BeforeYouBegin"></a> Перед началом  
  
###  <a name="Security"></a> Безопасность  
  
####  <a name="Permissions"></a> Разрешения  
 Требуется разрешение **CONTROL SERVER** .  
  
##  <a name="SSMSProcedure"></a> Использование среды SQL Server Management Studio  
  
#### Просмотр журнала подсистемы аудита SQL Server  
  
1.  В обозревателе объектов раскройте папку **Безопасность** .  
  
2.  Разверните папку **Аудит** .  
  
3.  Щелкните правой кнопкой мыши журнал аудита, который необходимо просмотреть, и выберите пункт **Просмотр журналов аудита**. Открывается диалоговое окно **Просмотр файла журнала —***имя_сервера*. Дополнительные сведения см. в статье [Log File Viewer F1 Help](../../../relational-databases/logs/log-file-viewer-f1-help.md).  
  
4.  После завершения нажмите кнопку **Закрыть**.  
  
 [!INCLUDE[msCoName](../../../includes/msconame-md.md)] рекомендует просматривать журнал аудита, используя средство просмотра файлов журнала. Однако при создании автоматизированной системы мониторинга информацию в файле аудита можно просматривать напрямую с помощью функции [sys.fn_get_audit_file (Transact-SQL)](../../../relational-databases/system-functions/sys-fn-get-audit-file-transact-sql.md). При чтении файла напрямую данные возвращаются в несколько ином (необработанном) формате. Дополнительные сведения см. в статье **sys.fn_get_audit_file**.  
  
## См. также:  
 [Подсистема аудита SQL Server (компонент Database Engine)](../../../relational-databases/security/auditing/sql-server-audit-database-engine.md)   
 [Запись событий подсистемы аудита SQL Server в журнал безопасности](../../../relational-databases/security/auditing/write-sql-server-audit-events-to-the-security-log.md)  
  
  