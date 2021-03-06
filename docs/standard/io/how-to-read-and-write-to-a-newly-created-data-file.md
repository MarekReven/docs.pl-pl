---
title: "Porady: odczyt i zapis we właśnie utworzonym pliku danych"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-standard
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- csharp
- vb
- cpp
helpviewer_keywords:
- streams, reading and writing data
- BinaryReader class, examples
- I/O [.NET Framework], reading data
- I/O [.NET Framework], writing data
- BinaryWriter class, examples
ms.assetid: e209d949-31e8-44ea-8e38-87f9093f3093
caps.latest.revision: "16"
author: mairaw
ms.author: mairaw
manager: wpickett
ms.workload:
- dotnet
- dotnetcore
ms.openlocfilehash: 04ded71a23ba4cabab0a22e0d66c1084a726d8c8
ms.sourcegitcommit: e7f04439d78909229506b56935a1105a4149ff3d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/23/2017
---
# <a name="how-to-read-and-write-to-a-newly-created-data-file"></a>Porady: odczyt i zapis we właśnie utworzonym pliku danych
<xref:System.IO.BinaryWriter> i <xref:System.IO.BinaryReader?displayProperty=nameWithType> klasy służą do zapisywania i odczytywania danych zamiast ciągów znaków. W poniższym przykładzie pokazano sposób zapisywania danych do i odczytać danych ze strumienia nowy, pusty plik o nazwie `Test.data`. Po utworzeniu pliku danych w bieżącym katalogu skojarzonego <xref:System.IO.BinaryWriter> i <xref:System.IO.BinaryReader> obiekty są tworzone i <xref:System.IO.BinaryWriter> obiektu służy do zapisywania liczb całkowitych od 0 do 10, aby `Test.data`, dlatego wskaźnika pliku na końcu plik. Po ustawieniu wskaźnika pliku z powrotem do źródła, <xref:System.IO.BinaryReader> obiektu odczytuje określony zawartość.  
  
## <a name="example"></a>Przykład  
 [!code-cpp[System.IO.BinaryReaderWriter#7](../../../samples/snippets/cpp/VS_Snippets_CLR_System/system.IO.BinaryReaderWriter/CPP/source6.cpp#7)]
 [!code-csharp[System.IO.BinaryReaderWriter#7](../../../samples/snippets/csharp/VS_Snippets_CLR_System/system.IO.BinaryReaderWriter/CS/source6.cs#7)]
 [!code-vb[System.IO.BinaryReaderWriter#7](../../../samples/snippets/visualbasic/VS_Snippets_CLR_System/system.IO.BinaryReaderWriter/VB/source6.vb#7)]  
  
## <a name="robust-programming"></a>Niezawodne programowanie  
 Jeśli `Test.data` już istnieje w bieżącym katalogu <xref:System.IO.IOException> wyjątku. Użyj opcji Tryb pliku <xref:System.IO.FileMode.Create?displayProperty=nameWithType> kiedy należy zainicjować strumień plików, aby zawsze twórz nowych plików bez generowania wyjątku.  
  
## <a name="see-also"></a>Zobacz też  
 <xref:System.IO.BinaryReader>  
 <xref:System.IO.BinaryWriter>  
 <xref:System.IO.FileStream>  
 <xref:System.IO.FileStream.Seek%2A?displayProperty=nameWithType>  
 <xref:System.IO.SeekOrigin>  
 [Instrukcje: wyliczanie katalogów i plików](../../../docs/standard/io/how-to-enumerate-directories-and-files.md)  
 [Instrukcje: otwieranie pliku dziennika i dołączanie do niego](../../../docs/standard/io/how-to-open-and-append-to-a-log-file.md)  
 [Instrukcje: odczytywanie tekstu z pliku](../../../docs/standard/io/how-to-read-text-from-a-file.md)  
 [Instrukcje: zapisywanie tekstu w pliku](../../../docs/standard/io/how-to-write-text-to-a-file.md)  
 [Instrukcje: odczytywanie znaków z ciągu](../../../docs/standard/io/how-to-read-characters-from-a-string.md)  
 [Instrukcje: zapisywanie znaków w ciągu](../../../docs/standard/io/how-to-write-characters-to-a-string.md)  
 [Plik i strumienia I-O](../../../docs/standard/io/index.md)
