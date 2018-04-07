---
title: Драйвер ODBC для Linux и macOS - высокого уровня доступности и аварийного восстановления | Документы Microsoft
ms.custom: ''
ms.date: 04/04/2018
ms.prod: sql-non-specified
ms.prod_service: drivers
ms.service: ''
ms.component: odbc
ms.reviewer: ''
ms.suite: sql
ms.technology:
- drivers
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: fa656c5b-a935-40bf-bc20-e517ca5cd0ba
caps.latest.revision: 16
author: MightyPen
ms.author: genemi
manager: jhubbard
ms.workload: Inactive
ms.openlocfilehash: e69df64ad4e5c5e5319719fe14f380c745b0aeba
ms.sourcegitcommit: 094c46e7fa6de44735ed0040c65a40ec3d951b75
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/06/2018
---
# <a name="odbc-driver-on-linux-and-macos-support-for-high-availability-and-disaster-recovery"></a>Драйвер ODBC для Linux и macOS поддержку высокого уровня доступности и аварийного восстановления
[!INCLUDE[Driver_ODBC_Download](../../../includes/driver_odbc_download.md)]

Драйверы ODBC для Linux и macOS поддержки [!INCLUDE[ssHADR](../../../includes/sshadr_md.md)]. Дополнительные сведения о [!INCLUDE[ssHADR](../../../includes/sshadr_md.md)], см.:  
  
-   [Прослушиватели группы доступности, возможность подключения клиентов и отработка отказа приложений (SQL Server)](http://msdn.microsoft.com/library/hh213417.aspx)  
  
-   [Создание и настройка группы доступности (SQL Server)](http://msdn.microsoft.com/library/ff878265.aspx)  
  
-   [Отказоустойчивая кластеризация и группы доступности AlwaysOn (SQL Server)](http://msdn.microsoft.com/library/ff929171.aspx)  
  
-   [Активные вторичные реплики: Для чтения вторичные реплики (группы доступности AlwaysOn)](http://msdn.microsoft.com/library/ff878253.aspx)  
  
Прослушиватель для заданной группы доступности можно задать в строке подключения. Если приложение ODBC в Linux или macOS подключен к базе данных в группе доступности, которая выполняет отработку отказа, то исходное соединение разрывается и приложение должно установить новое соединение для продолжения работы после отработки отказа.

Драйверы ODBC в Linux и macOS поочередно для всех IP-адресов, если вы не подключаетесь к прослушивателю группы доступности, и несколько IP-адресов, связанные с именем узла, связанного с DNS-имени узла.

Если DNS-сервер первый возвращенный IP-адрес не является доступным для подключения, продолжительность итераций может занять много времени. При подключении к прослушивателю группы доступности драйвер пытается установить соединения для всех IP-адресов в параллельном режиме. Если попытка соединения завершается успешно, драйвер отменяет все ожидающие попытки подключения.

> [!NOTE]  
> Так как подключение может завершиться ошибкой из-за отработки отказа группы доступности Реализуйте логику повторного соединения; Повторите ошибки соединения до достижения успеха. Увеличение времени ожидания соединения и реализация логики повторного соединения позволяют повысить вероятность соединения с группой доступности.

## <a name="connecting-with-multisubnetfailover"></a>Соединение с помощью MultiSubnetFailover

Всегда указывайте **MultiSubnetFailover = Yes** (или **= True**) при подключении к [!INCLUDE[ssSQL11](../../../includes/sssql11_md.md)] прослушивателя группы доступности или [!INCLUDE[ssSQL11](../../../includes/sssql11_md.md)] экземпляра отказоустойчивого кластера. **MultiSubnetFailover** обеспечивает ускоренную отработку отказа для всех групп доступности и экземпляра отказоустойчивого кластера в [!INCLUDE[ssSQL11](../../../includes/sssql11_md.md)]. **MultiSubnetFailover** также значительно сокращает время отработки отказа для топологий AlwaysOn с одной или несколькими подсетями. При отработке отказа в сети с несколькими подсетями клиент пытается установить соединения параллельно. При отработке отказа драйвер агрессивно повторяет попытки соединения по протоколу TCP.

Свойство соединения **MultiSubnetFailover** указывает, что приложение развертывается в группе доступности или экземпляре отказоустойчивого кластера. Драйвер пытается соединиться с базой данных на сервере-источнике [!INCLUDE[ssNoVersion](../../../includes/ssnoversion_md.md)] экземпляра, пытаясь подключиться ко всем IP-адресов. При соединении с **MultiSubnetFailover = Yes**, клиент повторяет попытку соединения по TCP быстрее, чем интервалов повторной передачи TCP операционной системы по умолчанию. **MultiSubnetFailover = Yes** позволяет ускорить восстановление соединения после отработки отказа группы доступности AlwaysOn или экземпляра отказоустойчивого кластера AlwaysOn. **MultiSubnetFailover = Yes** относятся к одним и несколькими подсетями группы доступности и экземпляров отказоустойчивых кластеров.  

Используйте **MultiSubnetFailover=Yes** при соединении с прослушивателем группы доступности или экземпляром отказоустойчивого кластера. В противном случае производительность приложения может снизиться.

При подключении к серверу в группе доступности или экземпляра отказоустойчивого кластера, обратите внимание на следующее:
  
-   Укажите **MultiSubnetFailover = Yes** для повышения производительности при соединении с одной или несколькими подсетями группы доступности.

-   Указывайте прослушиватель группы доступности группы доступности в качестве сервера в строке подключения.
  
-   Не удается подключиться к [!INCLUDE[ssNoVersion](../../../includes/ssnoversion_md.md)] экземпляр настроено более 64 IP-адресов.

-   Оба [!INCLUDE[ssNoVersion](../../../includes/ssnoversion_md.md)] проверку подлинности или проверку подлинности Kerberos можно использовать с **MultiSubnetFailover = Yes** без влияния на поведение приложения.

-   Значение **loginTimeout** можно увеличить с учетом времени отработки отказа, это уменьшит количество попыток повторного соединения в приложении.

-   Распределенные транзакции не поддерживаются.  
  
Если маршрутизация только для чтения неактивна, то подключение к расположению вторичной реплики в группе доступности завершается ошибкой в следующих случаях:  
  
1.  Если местоположение вторичных реплик не настроено для приема подключений.  
  
2.  Если приложение использует **ApplicationIntent=ReadWrite** и расположение вторичных реплик настроено для доступа только для чтения.  
  
При соединении происходит ошибка, если первичная реплика настроена на отклонение рабочих нагрузок только для чтения, а строка подключения содержит **ApplicationIntent=ReadOnly**.  


[!INCLUDE[specify-application-intent_read-only-routing](~/includes/paragraph-content/specify-application-intent-read-only-routing.md)]


## <a name="odbc-syntax"></a>Синтаксис ODBC

Два ключевых слов строки подключения ODBC поддерживают [!INCLUDE[ssHADR](../../../includes/sshadr_md.md)]:  
  
-   **ApplicationIntent**  
  
-   **MultiSubnetFailover**  
  
Дополнительные сведения о ключевых словах строки подключения ODBC см. в статье [Использование ключевых слов строки подключения с SQL Server Native Client](http://msdn.microsoft.com/library/ms130822.aspx).  
  
Перечислены атрибуты эквивалентного соединения.
  
-   **SQL_COPT_SS_APPLICATION_INTENT**  
  
-   **SQL_COPT_SS_MULTISUBNET_FAILOVER**  
  
Дополнительные сведения об атрибутах соединения ODBC см. в разделе [SQLSetConnectAttr](http://msdn.microsoft.com/library/ms131709.aspx).  
  
Приложения ODBC, который использует [!INCLUDE[ssHADR](../../../includes/sshadr_md.md)] можно использовать один из двух функций для подключения:  
  
|Функция|Описание|  
|------------|---------------|  
|[Функция SQLConnect](../../../odbc/reference/syntax/sqlconnect-function.md)|**SQLConnect** поддерживает **ApplicationIntent** и **MultiSubnetFailover** через атрибут соединения или имя источника данных (DSN).|  
|[Функция SQLDriverConnect](../../../odbc/reference/syntax/sqldriverconnect-function.md)|**SQLDriverConnect** поддерживает **ApplicationIntent** и **MultiSubnetFailover** через DSN, ключевое слово строки подключения или атрибут соединения.|
  
## <a name="see-also"></a>См. также  

[Ключевые слова строки подключения и имена источников данных (DSN)](../../../connect/odbc/linux-mac/connection-string-keywords-and-data-source-names-dsns.md)

[Указания по программированию](../../../connect/odbc/linux-mac/programming-guidelines.md)

[Заметки о выпуске](../../../connect/odbc/linux-mac/release-notes.md)  
