---
layout: default
title: FAQ
nav_order: 20
---

1. Why is my transfer to Dataverse not showing up as published?

**dryad2dataverse** does not _publish_ the dataset. That must still be done via the Dataverse GUI or API. 

Publication functionality has been intentionally omitted as there are file size limits within a default Dataverse installation that do not apply to Dryad, and Dataverse installations are [more] often subject to manual data curation.

1. Why does the code use camel case instead of snake case for variables?

By the time I realized I should be using snake case, it was too late and Iwas already consistently using camel case. <https://www.python.org/dev/peps/pep-0008/#a-foolish-consistency-is-the-hobgoblin-of-little-minds>

 
