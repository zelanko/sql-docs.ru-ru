---
title: MSSQLSERVER_21892 | Документация Майкрософт
ms.custom: ''
ms.date: 04/04/2017
ms.prod: sql
ms.reviewer: ''
ms.technology: supportability
ms.topic: language-reference
helpviewer_keywords:
- 21892 (Database Engine error)
ms.assetid: 199818e8-28f4-440e-ad85-7bea88f51153
author: MashaMSFT
ms.author: mathoma
ms.openlocfilehash: 9c1ca2058879507785f5d637f976bee506981972
ms.sourcegitcommit: da88320c474c1c9124574f90d549c50ee3387b4c
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 07/01/2020
ms.locfileid: "85780480"
---
# <a name="mssqlserver_21892"></a>MSSQLSERVER_21892
 [!INCLUDE [SQL Server](../../includes/applies-to-version/sqlserver.md)]
  
## <a name="details"></a>Сведения  
  
| attribute | Значение |  
| :-------- | :---- |  
|Название продукта|SQL Server|  
|Идентификатор события|21892|  
|Источник события|MSSQLSERVER|  
|Компонент|SQLEngine|  
|Символическое имя|SQLErrorNum21892|  
|Текст сообщения|Невозможно выполнить запрос к sys.availability_replicas в первичной группе доступности, связанной с виртуальной машиной %s для имен серверов реплик членов: error = %d, error message = %s.|  
  
## <a name="explanation"></a>Объяснение  
**sp_validate_replica_hosts_as_publishers** выполняет запрос к текущей первичной реплике группы доступности, связанной с перенаправленным издателем, чтобы определить, на каких экземплярах [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] размещены реплики-члены.  Если выполнить этот запрос не удается, возвращается ошибка 21892.  
  
Обычно **sp_validate_replica_hosts_as_publishers** вызывается при первом использовании временно связанного сервера, поэтому проблемы с подключением, если они есть, скорее всего проявятся именно при вызове **sp_validate_replica_hosts_as_publishers**. В отличие от **sp_validate_redirected_publisher**, **sp_validate_replica_hosts_as_publishers** использует связанный сервер, который всегда использует учетные данные вызывающей стороны для подключения к любому из узлов реплик группы доступности.  
  
## <a name="user-action"></a>Действие пользователя  
При запуске этой хранимой процедуры убедитесь, что имя входа, используемое при выполнении, действительно на всех репликах. У имени входа должны быть достаточные права на авторизацию для выполнения запросов к таблицам метаданных группы доступности, а также к таблицам метаданных подписки на реплике базы данных издателя.  
  
Просмотрите исходное сообщение об ошибке, на которое указывает ссылка, чтобы определить причину ошибки и соответствующие действия по ее исправлению.  
  
