---
title: "Не удалось обновить данные для подключения к данным в книге. Повторите попытку или обратитесь к системному администратору. Следующие соединения не удалось обновить: данные Power Pivot | Microsoft Docs"
ms.custom: ""
ms.date: "03/23/2017"
ms.prod: "sql-server-2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "analysis-services"
ms.tgt_pltfrm: ""
ms.topic: "reference"
ms.assetid: 0f6fd52d-ac72-43e3-aa08-05a2d2bb873d
caps.latest.revision: 18
author: "Minewiskan"
ms.author: "owend"
manager: "erikre"
---
# Не удалось обновить данные для подключения к данным в книге. Повторите попытку или обратитесь к системному администратору. Следующие соединения не удалось обновить: данные Power Pivot
  Применительно к книгам Excel, содержащим данные [!INCLUDE[ssGemini](../../includes/ssgemini-md.md)] , службы Excel возвращают эту ошибку, если при передаче запроса на соединение серверу [!INCLUDE[ssGemini](../../includes/ssgemini-md.md)] запрос завершается ошибкой.  
  
## Сведения  
  
|||  
|-|-|  
|Применимо для следующих объектов:|[!INCLUDE[ssGemini](../../includes/ssgemini-md.md)] для SharePoint|  
|Номер версии продукта|[!INCLUDE[ssKilimanjaro](../../includes/sskilimanjaro-md.md)], [!INCLUDE[ssSQL11](../../includes/sssql11-md.md)], [!INCLUDE[ssSQL14](../../includes/sssql14-md.md)]|  
|Причина|См. ниже.|  
|Текст сообщения|Не удалось обновить данные для подключения к данным в книге. Повторите попытку или обратитесь к системному администратору. Следующие соединения не удалось обновить: данные [!INCLUDE[ssGemini](../../includes/ssgemini-md.md)] .|  
  
## Описание проблемы и действия по ее разрешению  
 Службы Excel не могут установить соединение или загрузить данные [!INCLUDE[ssGemini](../../includes/ssgemini-md.md)] . Эта ошибка возникает, в частности, при следующих условиях.  
  
 **Сценарий 1: служба не запущена**  
  
 Не запущен экземпляр служб SQL Server Analysis Services ([!INCLUDE[ssGemini](../../includes/ssgemini-md.md)]). Истечение срока действия пароля стало причиной остановки выполнения службы. Дополнительные сведения об изменении пароля см. в разделах [Configure Power Pivot Service Accounts](../../analysis-services/power-pivot-sharepoint/configure-power-pivot-service-accounts.md) и [Start or Stop a Power Pivot for SharePoint Server](../../analysis-services/power-pivot-sharepoint/start-or-stop-a-power-pivot-for-sharepoint-server.md).  
  
 **Сценарий 2a: открытие более ранней версии книги на сервере**  
  
 Возможно, книга, которую вы пытаетесь открыть, создана в другой версии [!INCLUDE[ssGemini](../../includes/ssgemini-md.md)] для Excel для SQL Server 2008 R2. Наиболее вероятно, что указанный в строке подключения поставщик данных служб Analysis Services, отсутствует на компьютере, который обрабатывает этот запрос.  
  
 Если это так, в журнале ULS вы найдете следующее сообщение: "Сбой обновления для данных [!INCLUDE[ssGemini](../../includes/ssgemini-md.md)] в книге \<URL-адрес книги>", после которого отображается сообщение "Не удается установить соединение".  
  
 Чтобы определить версию книги, необходимо открыть ее в Excel и проверить, какой поставщик данных указан в строке подключения. Книга SQL Server 2008 R2 использует в качестве поставщика данных MSOLAP.4.  
  
 Для решения этой проблемы вы можете обновить книгу. В качестве альтернативы можно установить клиентские библиотеки из версии служб Analysis Services для SQL Server 2008 R2 на физических ПК, на которых запускается [!INCLUDE[ssGemini](../../includes/ssgemini-md.md)] для служб SharePoint или Excel. [Установка поставщика OLE DB служб Analysis Services на серверах SharePoint](http://msdn.microsoft.com/ru-ru/2c62daf9-1f2d-4508-a497-af62360ee859).  
  
 **Сценарий 2b: службы Excel выполняются на сервере приложений, на котором находится неправильная версия клиентских библиотек**  
  
 По умолчанию, SharePoint Server 2010 устанавливает на серверы приложений со службами Excel поставщик OLE DB для версии служб Analysis Services, предназначенной для SQL Server 2008. В ферме, которая поддерживает доступ к данным [!INCLUDE[ssGemini](../../includes/ssgemini-md.md)] , все физические серверы, на которых запущены приложения, запрашивающие данные [!INCLUDE[ssGemini](../../includes/ssgemini-md.md)] , например службы Excel и [!INCLUDE[ssGemini](../../includes/ssgemini-md.md)] для SharePoint, должны использовать более позднюю версию поставщика данных.  
  
 Серверы под управлением [!INCLUDE[ssGemini](../../includes/ssgemini-md.md)] для SharePoint автоматически получают обновленный поставщик OLE DB. Другие серверы, например такие, на которых запущен отдельный экземпляр служб Excel без служб [!INCLUDE[ssGemini](../../includes/ssgemini-md.md)] для SharePoint, установленных на этом же компьютере, должны быть исправлены, чтобы использовать клиентские библиотеки более новой версии. Дополнительные сведения см. в разделе [Установка поставщика OLE DB служб Analysis Services на серверах SharePoint](http://msdn.microsoft.com/ru-ru/2c62daf9-1f2d-4508-a497-af62360ee859).  
  
 **Сценарий 3: недоступен контроллер домена**  
  
 Причина может заключаться в том, что контроллер домена недоступен для проверки удостоверения пользователя. Для проверки подлинности пользователя SharePoint службе Claims to Windows Token Service требуется контроллер домена при каждом соединении. Служба Claims to Windows Token Service не использует кэшированные учетные данные. Она проверяет удостоверение пользователя для каждого соединения.  
  
 Подтвердить причину этой ошибки можно, открыв файл журнала SharePoint. Если в журналах SharePoint есть сообщение «Не удалось получить WindowsIdentity от IClaimsIdentity», то подлинность удостоверения пользователя не удалось проверить.  
  
 Чтобы решить эту проблему, присоедините компьютер к домену, в котором находится сервер [!INCLUDE[ssGemini](../../includes/ssgemini-md.md)] , или установите контроллер домена на локальный компьютер. Второе решение, установка контроллера домена, потребует создания локальных учетных записей домена для всех служб и пользователей. Для создаваемых учетных записей потребуется настроить учетные записи служб и разрешения SharePoint.  
  
 Установка контроллера домена на компьютер рекомендуется в случае, если стоит задача использовать [!INCLUDE[ssGemini](../../includes/ssgemini-md.md)] для SharePoint вне сети (автономно). Подробные инструкции по порядку использования [!INCLUDE[ssGemini](../../includes/ssgemini-md.md)] в режиме "вне сети" см. в записи блога "Taking your [!INCLUDE[ssGemini](../../includes/ssgemini-md.md)] server off the network" (Отключение сервера [!INCLUDE[ssGemini](../../includes/ssgemini-md.md)] от сети) на сайте [http://www.powerpivotgeek.com](http://go.microsoft.com/fwlink/?LinkId=184241).  
  
 **Сценарий 4: сервер работает нестабильно**  
  
 Одна или несколько служб могут находиться в несогласованном состоянии. В некоторых случаях решить эту проблему можно, выполнив команду IISRESET.  
  
  