---
tags:
  - X
tanggal: <% tp.date.now("YYYY-MM-DD") %>
cssclasses:
  - center-images
---
___
<% await tp.file.rename(`(${tp.date.now("YYYY-MM-DD")}) MATERI`)%>
<% tp.file.cursor() %>