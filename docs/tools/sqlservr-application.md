---
title: Приложение sqlservr | Документация Майкрософт
ms.custom: ''
ms.date: 03/14/2017
ms.prod: sql
ms.prod_service: sql-tools
ms.reviewer: ''
ms.technology: tools-other
ms.topic: conceptual
helpviewer_keywords:
- command prompt utilities [SQL Server], sqlservr
- command prompt [SQL Server], pausing/resuming instance of SQL Server
- starting instance of SQL Server
- command prompt [SQL Server], continuing instance of SQL Server
- sqlservr utility
- pausing instance of SQL Server
- stopping instance of SQL Server
- resuming SQL Server
- command prompt [SQL Server], stopping instance of SQL Server
- command prompt [SQL Server], starting instance of SQL Server
- continuing instance of SQL Server
ms.assetid: 60e8ef0a-0851-41cf-a6d8-cca1e04cbcdb
author: markingmyname
ms.author: maghan
manager: craigg
ms.openlocfilehash: 93a4572b44cf2be6fa8f1c0912fa7e8178e6c9a7
ms.sourcegitcommit: e0c55d919ff9cec233a7a14e72ba16799f4505b2
ms.translationtype: MTE75
ms.contentlocale: ru-RU
ms.lasthandoff: 07/10/2019
ms.locfileid: "67733358"
---
# <a name="sqlservr-application"></a>Приложение sqlservr
[!INCLUDE[appliesto-ss-xxxx-xxxx-xxx-md](../includes/appliesto-ss-xxxx-xxxx-xxx-md.md)]
  Приложение **sqlservr** позволяет запускать, останавливать, приостанавливать и возобновлять работу экземпляра [!INCLUDE[msCoName](../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] из командной строки.  
  
## <a name="syntax"></a>Синтаксис  
  
```  
  
sqlservr [-sinstance_name] [-c] [-dmaster_path] [-f]   
     [-eerror_log_path] [-lmaster_log_path] [-m]  
     [-n] [-Ttrace#] [-v] [-x] [-gnumber]  
```  
  
## <a name="arguments"></a>Аргументы  
 **-s** *instance_name*  
 Указывает экземпляр [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] для подключения. Если именованный экземпляр не указан, программа **sqlservr** запускает экземпляр [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)]по умолчанию.  
  
> [!IMPORTANT]  
>  Для запуска экземпляра [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)]приложение **sqlservr** необходимо запускать из каталога, соответствующего этому экземпляру. Для экземпляра по умолчанию **sqlservr** нужно запускать из каталога \MSSQL\Binn. Для именованного экземпляра **sqlservr** нужно запускать из каталога \MSSQL$*имя_экземпляра*\Binn.  
  
 **-c**  
 Указывает, что экземпляр [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] будет запущен независимо от диспетчера управления службами Microsoft Windows. Этот параметр используется при запуске [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] из командной строки, чтобы сократить время, необходимое для запуска [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] .  
  
> [!NOTE]  
>  При использовании этого параметра остановить [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] с помощью Service Manager [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] или команды **net stop** будет невозможно. [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] будет остановлен, если выйти из системы на данном компьютере.)  
  
 **-d** *master_path*  
 Указывает полный путь к файлу базы данных **master** . Между параметрами **-d** и *master_path*нет пробелов. Если этот параметр не задан, используются параметры из реестра.  
  
 **-f**  
 Запускает экземпляр [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] с минимальной конфигурацией. Эта функция полезна в случае, если установленные значения конфигурации (например, слишком большой объем выделяемой памяти) не позволяют выполнить запуск сервера.  
  
 **-e** *error_log_path*  
 Указывает полный путь к файлу журнала ошибок. Если путь не указан, расположением по умолчанию является *\<диск>* :\Program Files\Microsoft SQL Server\MSSQL\Log\Errorlog для экземпляра по умолчанию и *\<диск>* :\Program Files\Microsoft SQL Server\MSSQL$*имя_экземпляра*\Log\Errorlog — для именованного экземпляра. Между параметрами **-e** и *error_log_path*нет пробелов.  
  
 **-l** *master_log_path*  
 Указывает полный путь к файлу журнала транзакций базы данных **master** . Между параметрами **-l** и *master_log_path*нет пробелов.  
  
 **-m**  
 Указывается для запуска экземпляра [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] в однопользовательском режиме. Если [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] запущен в однопользовательском режиме, к нему может подключиться только один пользователь. Механизм CHECKPOINT, гарантирующий, что завершенные транзакции регулярно записываются из дискового кэша в устройство хранения базы данных, не запускается. (Как правило, этот параметр используется при появлении проблем с системными базами данных, требующими исправления.) Включает параметр **sp_configure allow updates**. По умолчанию параметр **allow updates** отключен.  
  
 **-n**  
 Позволяет запустить именованный экземпляр [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)]. Если не указать параметр **-s** , будет выполнена попытка запуска экземпляра по умолчанию. Перед запуском программы **sqlservr.exe**в командной строке необходимо перейти в каталог BINN соответствующего экземпляра. Например, если экземпляр Instance1 должен использовать \mssql$Instance1 для своих двоичных файлов, для запуска **sqlservr.exe -s instance1**пользователь должен быть в каталоге \mssql$Instance1\binn. Если экземпляр [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] запускается с параметром **-n** , целесообразно также использовать параметр **-e** , иначе события [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] не будут регистрироваться.  
  
 **-T** *trace#*  
 Указывает, что экземпляр [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] фактически должен запускаться с установленным флагом трассировки (*trace#* ). Флаги трассировки используются для запуска сервера в нестандартном режиме. Дополнительные сведения см. в разделе [Флаги трассировки (Transact-SQL)](../t-sql/database-console-commands/dbcc-traceon-trace-flags-transact-sql.md).  
  
> [!IMPORTANT]  
>  При указании флага трассировки укажите **-T**, чтобы передать номер флага трассировки. Знак t в нижнем регистре ( **-t**) также принимается [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)]. Однако в этом случае **-t** установит другие внутренние флаги трассировки, необходимые специалистам службы поддержки [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] .  
  
 **-v**  
 Отображает номер версии сервера.  
  
 **-x**  
 Отключает ведение статистики по процессорному времени и коэффициенту попадания в кэш. Позволяет достичь максимальной производительности.  
  
 **-g** *memory_to_reserve*  
 Определяет целое число мегабайтов (МБ) памяти, которую [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] оставляет доступной для распределения памяти в пределах процесса [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] , но за пределами пула памяти [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] . Память за пределами пула памяти является областью, используемой [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] для загрузки таких элементов, как `.dll` -файлы расширенных процедур, поставщики OLE DB, на которые ссылаются распределенные запросы, и объекты автоматизации, на которые имеется ссылка в инструкциях [!INCLUDE[tsql](../includes/tsql-md.md)] . По умолчанию установлено значение 256 МБ.  
  
 Использование данного параметра может помочь в настройке распределения памяти, но только в том случае, если объем физической памяти превышает предел, установленный операционной системой для виртуальной памяти, доступной для приложений. Использование данного параметра может быть полезным в конфигурациях с большим объемом памяти, где требования к использованию памяти [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] являются нетипичными и виртуальное пространство процесса [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] используется в полной мере. Неверное использование этого параметра может привести к появлению условий, при которых экземпляр [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] не будет запущен или может вызвать ошибки времени выполнения.  
  
 Используйте значение параметра **-g** по умолчанию, только если в файле журнала ошибок [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] не присутствуют следующие предупреждения:  
  
-   "Failed Virtual Allocate Bytes: FAIL_VIRTUAL_RESERVE \<size>" (Ошибка виртуального выделения байтов: FAIL_VIRTUAL_RESERVE \<размер>).  
  
-   "Failed Virtual Allocate Bytes: FAIL_VIRTUAL_COMMIT \<size>" (Ошибка виртуального выделения байтов: FAIL_VIRTUAL_COMMIT \<размер>).  
  
 Эти сообщения могут свидетельствовать о попытках [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] освободить часть пула памяти [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] , чтобы найти пространство для таких элементов, как dll-файлы расширенных хранимых процедур или объекты автоматизации. В этом случае рассмотрите возможность увеличения размера памяти, зарезервированной с помощью параметра **-g** .  
  
 Использование значения меньше, чем значение по умолчанию, увеличивает объем памяти, доступной для буферного пула и стеков потоков. Это может обеспечить некоторое повышение производительности при рабочих нагрузках, интенсивно использующих память в системах, использующих небольшое количество расширенных хранимых процедур, распределенных запросов или объектов автоматизации.  
  
## <a name="remarks"></a>Remarks  
 В большинстве случаев программа sqlserver.exe используется только для устранения неполадок или в ходе масштабных операций обслуживания. Если [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] запущен из командной строки с помощью программы sqlservr.exe, [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] запускается не в качестве службы, поэтому остановить [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] с помощью команды **net** невозможно. Пользователи могут подключаться к [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)], однако средства [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] отображают состояние службы, поэтому диспетчер конфигурации [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] правильно показывает, что служба остановлена. [!INCLUDE[ssManStudioFull](../includes/ssmanstudiofull-md.md)] может подключаться к серверу, но также укажет, что служба остановлена.  
  
## <a name="compatibility-support"></a>Поддержка совместимости  
 Параметр **-h**  не поддерживается в [!INCLUDE[ssCurrent](../includes/sscurrent-md.md)]. Этот параметр использовался в более ранних версиях 32-битных экземпляров [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] для резервирования виртуального адресного пространства для метаданных памяти с «горячей» заменой при включенных расширениях AWE. Дополнительные сведения см. в разделе [Неподдерживаемые функции SQL Server 2016](https://msdn.microsoft.com/library/0678bfbc-5d3f-44f4-89c0-13e8e52404da).  
  
## <a name="see-also"></a>См. также:  
 [Параметры запуска службы Database Engine](../database-engine/configure-windows/database-engine-service-startup-options.md)  
  
  
