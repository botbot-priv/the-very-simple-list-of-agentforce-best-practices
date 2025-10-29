## Pattern: Narrow, Curated Knowledge beats “Index Everything”

**Intent**  
Improve answer quality and reduce costs by scoping retrieval to a **small, curated** knowledge set aligned to a **specific question set**.

---

### ✅ What Works
- **Be specific.** Frame the challenge.  
  For example: “We need an Agent to answer our 10 most-asked customer questions, at the right time, using relevant knowledge.”
- **Small, curated knowledge sets** (like a single FAQ object) **>** 100GB of unreviewed docs.

### ⚠️ What Breaks
- Expecting an Agent to be an *all-knowing oracle*.  
- Ingesting massive, unreviewed & unstructured data sets.  
- Skipping **pre/post filtering** ⇒ poor quality + high cost.

### 💡 Implications
- RAG at scale is often **fragile and expensive**.  
- **More data ≠ better answers.**  
- A **narrow scope** often wins: faster, cheaper, more reliable.  
- Overpromising frustrates customers when “AI knows everything” fails.

### 📌 Guiding Principle
If you wouldn’t train a **human** with that messy knowledge base, don’t expect an **AI Agent** to succeed either.