<%*
  let title = tp.file.title
  if (title.startsWith("Untitled")) {
    title = await tp.system.prompt("Title");
    await tp.file.rename(title);
  } 
  
  tR += "---"
%>
title:  <%* tR += title %>
date: <% tp.date.now("YYYY-MM-D") %>
lastmod: <% tp.file.last_modified_date("YYYY-MM-D") %>
draft: true
tags: ["tag1","tag2"]
categories: ["cat1", "cat2"]
---
# <%* tR += title %>