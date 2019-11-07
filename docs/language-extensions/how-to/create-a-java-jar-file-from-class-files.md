---
title: Создание JAR-файла Java из файлов класса
titleSuffix: SQL Server Language Extensions
description: Узнайте, как создать JAR-файл Java из файлов класса
author: dphansen
ms.author: davidph
ms.date: 07/25/2019
ms.topic: conceptual
ms.prod: sql
ms.technology: language-extensions
monikerRange: '>=sql-server-ver15||>=sql-server-linux-ver15||=sqlallproducts-allversions'
ms.openlocfilehash: 4cec311a28f9d5119b5a0aeb696597e8b34ba25a
ms.sourcegitcommit: a154b3050b6e1993f8c3165ff5011ff5fbd30a7e
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 07/30/2019
ms.locfileid: "73588778"
---
# <a name="create-a-java-jar-file-from-class-files"></a>Создание JAR-файла Java из файлов класса
[!INCLUDE[appliesto-ss-xxxx-xxxx-xxx-md](../../includes/appliesto-ss-xxxx-xxxx-xxx-md.md)]

При использовании [языковых расширений SQL Server](../language-extensions-overview.md) и выполнении кода Java рекомендуется упаковать файлы класса в JAR-файл.

## <a name="create-a-jar-file"></a>Создание JAR-файла

Чтобы создать JAR-файл из файлов класса, перейдите в папку с файлом класса и выполните следующую команду:

```cmd
jar -cf <MyJar.jar> *.class
```

Убедитесь, что путь к `jar.exe` включен в системную переменную PATH. Либо укажите полный путь к этому файлу, который расположен в подпапке `/bin` папки JDK. Пример:

```cmd
C:\Users\MyUser\Desktop\jdk1.8.0_201\bin\jar -cf <MyJar.jar> *.class
```

## <a name="next-steps"></a>Дальнейшие действия

+ [Как вызвать код Java в SQL Server](../how-to/call-java-from-sql.md)