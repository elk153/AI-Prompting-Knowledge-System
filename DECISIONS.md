# Decision Backlog --- Lesson Generation

**Version:** 1.0\
**Date:** 2026-11-14

## How to use this backlog

Each decision represents a learning unit to be executed. Executing one
decision generates exactly one lesson using `LESSON_TEMPLATE.md`.

**Execution command:** `Execute decision D001`

### Status definitions

-   `PROPOSED` --- identified in the roadmap.
-   `READY` --- prerequisites and references are sufficient.
-   `IN_PROGRESS` --- lesson generation/review is underway.
-   `GENERATED` --- draft lesson exists; not yet quality-checked.
-   `REVIEWED` --- lesson passed the quality gate.
-   `COMPLETED` --- exercises/evaluation completed and result recorded.
-   `BLOCKED` --- prerequisite, evidence or tool issue prevents
    progress.

## Backlog

  ------------------------------------------------------------------------------------
  ID                   Level Chapter     Decision / lesson  Dependencies   Status
                                         outcome                           
  ----------- -------------- ----------- ------------------ -------------- -----------
  D001                     1 1           Establish a        ---            GENERATED
                                         practical mental                  
                                         model of LLMs,                    
                                         capabilities and                  
                                         limitations                       

  D002                     1 2           Build a reusable   D001           PROPOSED
                                         outcome-first                     
                                         prompt structure                  

  D003                     1 2           Specify context,   D002           PROPOSED
                                         constraints,                      
                                         output contracts                  
                                         and acceptance                    
                                         criteria                          

  D004                     1 3           Improve prompts    D002           PROPOSED
                                         through                           
                                         disciplined                       
                                         iteration and                     
                                         clarification                     

  D005                     2 4           Engineer context   D003           PROPOSED
                                         and ground answers                
                                         in trusted                        
                                         information                       

  D006                     2 4           Detect and manage  D005           PROPOSED
                                         untrusted content                 
                                         and                               
                                         prompt-injection                  
                                         risks                             

  D007                     2 5           Analyse and        D005           PROPOSED
                                         extract                           
                                         information from                  
                                         complex documents                 

  D008                     2 5           Compare and        D007           PROPOSED
                                         synthesise                        
                                         information across                
                                         document                          
                                         collections                       

  D009                     2 6           Generate           D003, D007     PROPOSED
                                         professional                      
                                         documents with                    
                                         quality and                       
                                         traceability                      
                                         controls                          

  D010                     2 7           Select models,     D001           PROPOSED
                                         tools and                         
                                         operating modes                   
                                         for different task                
                                         classes                           

  D011                     3 8           Use AI for data    D005, D010     PROPOSED
                                         profiling,                        
                                         analysis and                      
                                         structured                        
                                         information                       
                                         management                        

  D012                     3 9           Direct AI coding   D003, D010     PROPOSED
                                         workflows and                     
                                         verify generated                  
                                         code                              

  D013                     3 10          Work effectively   D010           PROPOSED
                                         with image, audio,                
                                         video and                         
                                         mixed-modal inputs                

  D014                     3 11          Design prompt      D004           PROPOSED
                                         evaluations,                      
                                         rubrics and                       
                                         regression tests                  

  D015                     4 12          Design reliable    D014           PROPOSED
                                         multi-step AI                     
                                         workflows and                     
                                         prompt chains                     

  D016                     4 13          Design bounded     D010, D015     PROPOSED
                                         agentic workflows                 
                                         with tools and                    
                                         approvals                         

  D017                     4 14          Apply security,    D006, D014,    PROPOSED
                                         privacy, safety    D016           
                                         and reliability                   
                                         controls                          

  D018                     5 15          Build an           D010, D017     PROPOSED
                                         enterprise AI                     
                                         adoption and                      
                                         governance                        
                                         approach                          

  D019                     5 16          Manage             D014, D018     PROPOSED
                                         prompt/workflow                   
                                         portfolios,                       
                                         versions and                      
                                         performance                       

  D020                     5 17          Deliver an         D011--D019     PROPOSED
                                         end-to-end                        
                                         AI-enabled                        
                                         workflow capstone                 
  ------------------------------------------------------------------------------------

## Execution protocol

For each decision:

1.  Confirm the decision ID, title, chapter, dependencies and status.
2.  Read the corresponding roadmap scope, lesson template and
    references.
3.  Generate one lesson file named `L###-short-title.md`. Lesson
    numbering should follow decision numbering (`L001` for `D001`).
4.  Ensure the lesson includes measurable objectives, rationale,
    references, exercises, expected outputs, evaluation grid and
    completion criteria.
5.  Validate source links and ensure exercises can actually be performed
    with accessible tools.
6.  Review the lesson against the quality gate in `README.md`.
7.  Update this decision's status and add a dated execution note below.
8.  Do not automatically execute the next decision.

## Execution history

  Date   Decision   Lesson file   Status                      Assessment / notes
  ------ ---------- ------------- --------------------------- -------------------------
  2026-11-14 D001       L001-mental-models-of-llms.md GENERATED    Lesson generated and reviewed against README quality gate; source links checked; learner exercises and assessment remain pending.

## Change log

-   2026-11-14 --- v1.1: Executed D001; generated and reviewed L001. Status set to GENERATED because learner exercises and assessment are not yet complete.
-   2026-11-14 --- v1.0: Initial 20-decision backlog created from the
    17-chapter roadmap.
