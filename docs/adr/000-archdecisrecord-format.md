1. Architecture Decision Records (ADRs)
This is the industry-standard pattern for exactly what you're describing — documenting why you chose something, not just what you built. Each decision gets its own small file:

docs/adr/
  0001-use-mongodb-over-postgres.md
  
  0002-jwt-auth-over-sessions.md
  
  0003-recurring-appointment-model.md
  

Each ADR follows a tiny template: Context → Decision → Consequences → Status (proposed/accepted/superseded). When you change your mind later, you don't delete the old one — you write a new ADR that supersedes it. That trail of "I thought X, then learned Y, so I switched to Z" is genuinely valuable later (and looks great in a portfolio project since it shows SSDLC thinking, not just code).
