# Articles

- [If you do microservices correctly, you don't need a workflow engine or BPMN](https://blog-codecentric-de.translate.goog/wer-microservices-richtig-macht-braucht-keine-workflow-engine-und-kein-bpmn?_x_tr_sl=de&_x_tr_tl=en&_x_tr_hl=en&_x_tr_pto=wapp)   -- Great blog post from 2015. It's a Google Translate link, the original is in German: [Wer Microservices richtig macht, braucht keine Workflow Engine und kein BPMN](https://blog.codecentric.de/wer-microservices-richtig-macht-braucht-keine-workflow-engine-und-kein-bpmn)

- [Refactor from Monolith Workflow to Micro-Workflows](https://itnext.io/refactor-from-monolith-workflow-to-micro-workflows-92afcc49c8ec) -- As far as I can tell, the author of this blog post coined the term "microworkflow".

- [Orchestration vs choreography for microservice workflows](https://www.ben-morris.com/orchestration-vs-choreography-for-microservice-workflows/) -- find a quote from this blog post below.


# Quotes

> _No shiny "workflow platform" can solve the problem of mega-workflows being a 
> maintenance nightmare, and a shady place where the responsibilities of the 
> parties are not clear - as everybody claims - the workflow is it's own 
> thing, but then again there is no team responsible for such workflow.
> So I think tool matters less. The process is important.
> Same way we are splitting the monolith into bounded contexts in DDD, or into 
> micro-services from process/org structure perspective, mega workflows
> spanning many such microservices better be split as well, with very 
> clear boundaries around micro-workflows, and clearly defined 
> interfaces between them._

Kiril Chilingarashvili on [LinkedIn](https://www.linkedin.com/feed/update/urn:li:activity:7013454155839148032?commentUrn=urn%3Ali%3Acomment%3A%28activity%3A7013454155839148032%2C7018321388465774592%29&replyUrn=urn%3Ali%3Acomment%3A%28activity%3A7013454155839148032%2C7018323494476152832%29)


_One problem with orchestration is that it tends to give rise to complex infrastructure. A centralised orchestrator service needs to implement a range of concerns, including control flow, routing, connectivity, retries, data transformation, monitoring and reporting. This can give rise to runaway complexity over time as integration logic accumulates in a central integration platform._

Ben Morris, see "Orchestration vs choreography for microservice workflows" above.
