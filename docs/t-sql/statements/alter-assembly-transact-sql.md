---
title: "Инструкцию ALTER ASSEMBLY (Transact-SQL) | Документы Microsoft"
ms.custom: 
ms.date: 04/19/2017
ms.prod: sql-non-specified
ms.prod_service: sql-database
ms.service: 
ms.component: t-sql|statements
ms.reviewer: 
ms.suite: sql
ms.technology: database-engine
ms.tgt_pltfrm: 
ms.topic: language-reference
f1_keywords:
- ALTER_ASSEMBLY_TSQL
- ALTER ASSEMBLY
dev_langs: TSQL
helpviewer_keywords:
- assemblies [CLR integration], modifying
- refreshing assemblies
- assemblies [CLR integration], versioning
- assemblies [CLR integration], adding files
- modifying assemblies
- adding files
- ALTER ASSEMBLY statement
ms.assetid: 87bca678-4e79-40e1-bb8b-bd5ed8f34853
caps.latest.revision: "76"
author: JennieHubbard
ms.author: jhubbard
manager: jhubbard
ms.workload: On Demand
ms.openlocfilehash: 0b1a0a6da27bc534e22da2995fa592d6b430d418
ms.sourcegitcommit: 66bef6981f613b454db465e190b489031c4fb8d3
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 11/17/2017
---
# <a name="alter-assembly-transact-sql"></a>ALTER ASSEMBLY (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-xxxx-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-xxxx-xxxx-xxx-md.md)]

  Изменяет сборку, изменяя при этом свойства каталога [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] сборки. ALTER ASSEMBLY обновляет ее до последней копии [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[dnprdnshort](../../includes/dnprdnshort-md.md)] модулей, содержащих ее реализацию и добавляет или удаляет файлы, связанные с ним. Сборки создаются с помощью [CREATE ASSEMBLY](../../t-sql/statements/create-assembly-transact-sql.md).  

>  [!WARNING]
>  Среда CLR использует управление доступом для кода (CAS) в .NET Framework, которое больше не поддерживается в качестве границы безопасности. Сборки среды CLR, созданные с помощью `PERMISSION_SET = SAFE`, могут получать доступ к внешним системным ресурсам, вызывать неуправляемый код и получать права системного администратора. Начиная с [!INCLUDE[sssqlv14-md](../../includes/sssqlv14-md.md)], появился параметр `sp_configure`, называемый `clr strict security`, для повышения безопасности сборок среды CLR. `clr strict security` включен по умолчанию и рассматривает сборки `SAFE` и `EXTERNAL_ACCESS`, как если бы они были помечены `UNSAFE`. Параметр `clr strict security` можно отключить для обеспечения обратной совместимости, но это делать не рекомендуется. Корпорация Майкрософт рекомендует подписывать все сборки с помощью сертификата или асимметричного ключа с соответствующим именем входа, которому предоставлено разрешение `UNSAFE ASSEMBLY` в базе данных master. Дополнительные сведения см. в статье о параметре [clr strict security](../../database-engine/configure-windows/clr-strict-security.md).  

 ![Значок ссылки на раздел](../../database-engine/configure-windows/media/topic-link.gif "Значок ссылки на раздел") [Синтаксические обозначения в Transact-SQL](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
  
## <a name="syntax"></a>Синтаксис  
  
```  
ALTER ASSEMBLY assembly_name  
    [ FROM <client_assembly_specifier> | <assembly_bits> ]  
    [ WITH <assembly_option> [ ,...n ] ]  
    [ DROP FILE { file_name [ ,...n ] | ALL } ]  
    [ ADD FILE FROM   
    {   
        client_file_specifier [ AS file_name ]   
      | file_bits AS file_name   
    } [,...n ]   
    ] [ ; ]  
<client_assembly_specifier> :: =  
    '\\computer_name\share-name\[path\]manifest_file_name'  
  | '[local_path\]manifest_file_name'  
  
<assembly_bits> :: =  
    { varbinary_literal | varbinary_expression }  
  
<assembly_option> :: =  
    PERMISSION_SET = { SAFE | EXTERNAL_ACCESS | UNSAFE }   
  | VISIBILITY = { ON | OFF }  
  | UNCHECKED DATA  
  
```  
  
## <a name="arguments"></a>Аргументы  
 *assembly_name*  
 Имя сборки, которую нужно изменить. *assembly_name* уже должен существовать в базе данных.  
  
 ИЗ \<client_assembly_specifier > | \<assembly_bits >  
 Обновляет сборку до последней копии модулей платформы [!INCLUDE[dnprdnshort](../../includes/dnprdnshort-md.md)], содержащих ее реализацию. Этот параметр может использоваться при условии, что файлы, связанные с указанной сборкой, отсутствуют.  
  
 \<client_assembly_specifier > задает сетевое или локальное расположение, где находится обновляемая сборка. Сетевое расположение содержит имя компьютера, имя общей папки и путь внутри этой папки. *manifest_file_name* указывает имя файла, содержащего манифест сборки.  
  
 \<assembly_bits > является двоичным значением для сборки.  
  
 Для зависимых сборок, также нуждающихся в обновлении, должны выполняться отдельные инструкции ALTER ASSEMBLY.  
  
 PERMISSION_SET = { SAFE | EXTERNAL_ACCESS | UNSAFE }   
>  [!IMPORTANT]  
>  `PERMISSION_SET` Влияет параметр `clr strict security` описанному выводит предупреждение об открытии. Когда `clr strict security` — включена, все сборки, считаются `UNSAFE`.  
 Указывает для сборки свойство набора разрешений на доступ к коду [!INCLUDE[dnprdnshort](../../includes/dnprdnshort-md.md)]. Дополнительные сведения об этом свойстве см. в разделе [CREATE ASSEMBLY &#40; Transact-SQL &#41; ](../../t-sql/statements/create-assembly-transact-sql.md).  
  
> [!NOTE]  
>  Параметры EXTERNAL_ACCESS и UNSAFE недоступны в автономной базе данных.  
  
 VISIBILITY = { ON | OFF }  
 Указывает, видима ли сборка для создания на ее основе функций среды CLR, хранимых процедур, триггеров, определяемых пользователем типов и определяемых пользователем агрегатных функций. При установке OFF сборка может быть вызвана только при помощи других сборок. Если имеются объекты базы данных среды CLR, уже созданные с помощью сборки, ее видимость не может быть изменена. Все сборки, на который указывает *assembly_name* передаются как не отображается по умолчанию.  
  
 UNCHECKED DATA  
 По умолчанию инструкция ALTER ASSEMBLY не выполняется в том случае, если она должна проверять согласованность отдельных строк таблицы. Этот параметр позволяет впоследствии провести позже при помощи инструкции DBCC CHECKTABLE. Если данный параметр указан, [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] выполняет инструкцию ALTER ASSEMBLY даже в случае, если в базе данных имеются таблицы, содержащие:  
  
-   материализованные вычисляемые столбцы, которые непосредственно или косвенно ссылаются на методы в сборке при помощи функций или методов языка [!INCLUDE[tsql](../../includes/tsql-md.md)];  
  
-   ограничения CHECK, которые непосредственно или косвенно ссылаются на методы в сборке;  
  
-   Столбцы определяемого пользователем типа CLR, зависящих от сборки и типов, реализующих **UserDefined** (отличных**собственного**) формат сериализации.  
  
-   столбцы определяемого пользователем типа данных CLR, ссылающиеся на представления, созданные при помощи ключевого слова WITH SCHEMABINDING.  
  
 Любые имеющиеся ограничения CHECK отключаются и помечаются как ненадежные. Таблицы, содержащие столбцы, зависящие от сборки, помечаются как содержащие непроверенные данные, и сохраняют эту метку до тех пор, пока не будут проверены явно.  
  
 Только члены **db_owner** и **db_ddlowner** этот параметр можно указать предопределенные роли базы данных.  
  
 Требуется **разрешение ALTER ANY SCHEMA** разрешения для настройки этого параметра.  
  
 Дополнительные сведения см. в разделе [реализации сборки](../../relational-databases/clr-integration/assemblies-implementing.md).  
  
 [DROP FILE { *имя_файла*[ **,***.. .n*] | ВСЕ}]  
 Удаляет из базы данных файл, связанный со сборкой, или все файлы, связанные со сборкой. Если следующей является инструкция ADD FILE, инструкция DROP FILE выполняется в первую очередь. Это позволяет заменить файл другим файлом с тем же именем.  
  
> [!NOTE]  
>  Этот параметр недоступен в автономной базе данных.  
  
 [ADD FILE FROM { *client_file_specifier* [AS *имя_файла*] | *file_bits*AS *имя_файла*}  
 Передает на файлы для связывания со сборкой, такие как исходный код, файлы отладки или другие связанные сведения на сервер и делает их видимыми в **sys.assembly_files** представления каталога. *client_file_specifier* указывает расположение, из которого требуется отправить файл. *file_bits* можно использовать для указания списка двоичных значений, составляющих файл. *имя_файла* указывает имя, под которым файл должны храниться в экземпляре [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]. *имя_файла* должен быть указан, если *file_bits* указано и является необязательным при *client_file_specifier* указано. Если *имя_файла* не указан, часть file_name *client_file_specifier* используется в качестве *имя_файла*.  
  
> [!NOTE]  
>  Этот параметр недоступен в автономной базе данных.  
  
## <a name="remarks"></a>Замечания  
 Инструкция ALTER ASSEMBLY не нарушает сеансы, в которых в настоящий момент работает код изменяемой сборки. Текущие сеансы завершают выполнение с неизмененной сборкой.  
  
 Если указывается предложение FROM, инструкция ALTER ASSEMBLY обновляет сборку в соответствии с последними предоставленными копиями модулей. Так как в экземпляре [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] могут быть функции среды CLR, хранимые процедуры, триггеры, типы данных и пользовательские агрегатные функции, уже использующие сборку, инструкция ALTER ASSEMBLY привязывает их к последней реализации сборки. Для выполнения этой привязки в измененной сборке должны существовать методы с подписями, с которыми сопоставлены функции CLR, хранимые процедуры и триггеры. Классы, реализующие определяемые пользователем типы данных CLR и пользовательские агрегатные функции, должны удовлетворять требованиям для определяемых пользователем типов или агрегатных функций.  
  
> [!CAUTION]  
>  Если не указан параметр WITH UNCHECKED DATA, то [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] старается избежать выполнения ALTER ASSEMBLY, если сборка новой версии изменяет существующие данные в таблицах, индексах и т. д. Однако при обновлении сборки в среде CLR [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] не обеспечивает согласованности вычисляемых столбцов, указателей, индексированных представлений или выражений с базовыми процедурами или типами. Выполняйте инструкции ALTER ASSEMBLY с осторожностью, чтобы избежать несоответствия результата выражения и его значения, хранящегося в сборке.  
  
 Инструкция ALTER ASSEMBLY изменяет версию сборки. Культура и токен открытого ключа сборки не изменяются.  
  
 С помощью инструкции ALTER ASSEMBLY нельзя изменить:  
  
-   Подписи функций CLR, агрегатных функций, хранимых процедур и триггеров в экземпляре [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)], на которые ссылается сборка. Инструкция ALTER ASSEMBLY не выполняется, если [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] не может связать объекты базы данных [!INCLUDE[dnprdnshort](../../includes/dnprdnshort-md.md)] в [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] с новой версией сборки.  
  
-   Подписи методов сборки, вызываемых из других сборок.  
  
-   Список сборок, зависящих от сборки, как указано в **DependentList** свойства сборки.  
  
-   Возможность использования индексов в методе и в том числе, если только не существует индексов или постоянных вычисляемых столбцов, прямо или косвенно зависящих от этого метода.  
  
-   **FillRow** атрибут имени метода для функций CLR, возвращающие табличные значения.  
  
-   **Accumulate** и **Terminate** подпись метода для определяемых пользователем статистических функций.  
  
-   Системные сборки.  
  
-   Владение сборкой. Используйте [ALTER AUTHORIZATION &#40; Transact-SQL &#41; ](../../t-sql/statements/alter-authorization-transact-sql.md) вместо него.  
  
 Кроме того, для сборок, реализующих определяемые пользователем типы, с помощью инструкции ALTER ASSEMBLY можно выполнять только следующие изменения:  
  
-   изменение общих методов класса определяемого пользователем типа, если только не изменяются подписи или атрибуты;  
  
-   добавление новых общих методов;  
  
-   изменение приватных методов любым образом.  
  
 Поля в определяемом пользователем типе с собственной сериализацией, в том числе элементы данных или основные классы, с помощью инструкции ALTER ASSEMBLY изменить нельзя. Любые другие изменения не поддерживаются.  
  
 Если предложение ADD FILE FROM не указано, инструкция ALTER ASSEMBLY удаляет все файлы, связанные со сборкой.  
  
 Если инструкция ALTER ASSEMBLY выполняется без предложения UNCHECKED для данных, выполняются проверки того, что новая версия сборки не влияет на существующие данные в таблицах. В зависимости от объема данных, для которых необходима проверка, это может повлиять на производительность.  
  
## <a name="permissions"></a>Permissions  
 Необходимо разрешение ALTER на сборку. Дополнительные требования.  
  
-   Для изменения сборки, права которого существующий набор является EXTERNAL_ACCESS, требует**EXTERNAL ACCESS ASSEMBLY**разрешение на сервере.  
  
-   Для изменения разрешений, существующей сборки задано UNSAFE требует **UNSAFE ASSEMBLY** разрешение на сервере.  
  
-   Для изменения набора разрешений сборки на EXTERNAL_ACCESS требуется**EXTERNAL ACCESS ASSEMBLY** разрешение на сервере.  
  
-   Для изменения набора разрешений сборки на UNSAFE, необходимо **UNSAFE ASSEMBLY** разрешение на сервере.  
  
-   Требуется указать WITH UNCHECKED DATA, **разрешение ALTER ANY SCHEMA** разрешение.  


### <a name="permissions-with-clr-strict-security"></a>Разрешения с помощью строгой безопасности среды CLR    
Следующие разрешения, необходимые для изменения сборки среды CLR при `CLR strict security` включен:

- Пользователь должен иметь разрешение `ALTER ASSEMBLY`.  
- Кроме того, должно выполняться одно из следующих условий:  
  - Сборка должна была подписана сертификатом или асимметричным ключом, имеющим соответствующее имя входа с разрешением `UNSAFE ASSEMBLY` на сервере. Рекомендуется использовать подпись сборки.  
  - База данных имеет `TRUSTWORTHY` свойство со значением `ON` и базы данных, принадлежащие имени входа, имеющем разрешение `UNSAFE ASSEMBLY` на сервере. Использовать этот параметр не рекомендуется.  
  
  
 Дополнительные сведения о наборах разрешений сборки см. в разделе [проектирование сборки](../../relational-databases/clr-integration/assemblies-designing.md).  
  
## <a name="examples"></a>Примеры  
  
### <a name="a-refreshing-an-assembly"></a>A. Обновление сборки  
 На следующем примере показано, как сборка `ComplexNumber` обновляется до последней копии модулей [!INCLUDE[dnprdnshort](../../includes/dnprdnshort-md.md)], содержащих ее реализацию.  
  
> [!NOTE]  
>  Сборка `ComplexNumber` может быть создана при выполнении образцов скриптов UserDefinedDataType. Дополнительные сведения см. в разделе [определяемый пользователем тип](http://msdn.microsoft.com/library/a9b75f36-d7f5-47f7-94d6-b4448c6a2191).  
  
 ```
 ALTER ASSEMBLY ComplexNumber 
 FROM 'C:\Program Files\Microsoft SQL Server\130\Tools\Samples\1033\Engine\Programmability\CLR\UserDefinedDataType\CS\ComplexNumber\obj\Debug\ComplexNumber.dll' 
  ```
### <a name="b-adding-a-file-to-associate-with-an-assembly"></a>Б. Добавление файла, связанного со сборкой  
 На следующем примере показано, как производится передача файла с исходным кодом `Class1.cs`, связанного со сборкой `MyClass`. При этом предполагается, что сборка `MyClass` уже создана в базе данных.  
  
```  
ALTER ASSEMBLY MyClass   
ADD FILE FROM 'C:\MyClassProject\Class1.cs';  
```  
  
### <a name="c-changing-the-permissions-of-an-assembly"></a>В. Изменение разрешений сборки  
 На следующем примере показано, как набор разрешений сборки `ComplexNumber` меняется с SAFE на `EXTERNAL ACCESS`.  
  
```  
ALTER ASSEMBLY ComplexNumber WITH PERMISSION_SET = EXTERNAL_ACCESS;  
```  
  
## <a name="see-also"></a>См. также:  
 [СОЗДАТЬ СБОРКУ &#40; Transact-SQL &#41;](../../t-sql/statements/create-assembly-transact-sql.md)   
 [УДАЛИТЬ СБОРКУ &#40; Transact-SQL &#41;](../../t-sql/statements/drop-assembly-transact-sql.md)   
 [EVENTDATA (Transact-SQL)](../../t-sql/functions/eventdata-transact-sql.md)  
  
  
