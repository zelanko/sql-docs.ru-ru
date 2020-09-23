---
title: Создание JAR-файла Java из файлов класса
description: Упаковывайте файлы класса в JAR-файл при использовании расширений языка SQL Server для выполнения кода Java.
author: dphansen
ms.author: davidph
ms.date: 11/05/2019
ms.topic: conceptual
ms.prod: sql
ms.technology: language-extensions
monikerRange: '>=sql-server-ver15||>=sql-server-linux-ver15||=sqlallproducts-allversions'
ms.openlocfilehash: c324fca6893af35cafe6e9f65eccd0e8a0e478f9
ms.sourcegitcommit: 9b41725d6db9957dd7928a3620fe4db41eb51c6e
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 08/13/2020
ms.locfileid: "88180287"
---
# <a name="create-a-java-jar-file-from-class-files"></a>Создание JAR-файла Java из файлов класса
[!INCLUDE [SQL Server 2019 and later](../../includes/applies-to-version/sqlserver2019.md)]

Сведения о том, как упаковывать файлы класса в JAR-файл при использовании [расширений языка SQL Server](../language-extensions-overview.md) для выполнения кода Java. Рекомендуется упаковывать файлы.

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

+ [Вызов среды выполнения Java в расширениях языка SQL Server](../how-to/call-java-from-sql.md)