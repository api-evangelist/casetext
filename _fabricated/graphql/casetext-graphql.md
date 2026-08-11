# Casetext GraphQL Schema

## Overview

This conceptual GraphQL schema models the Casetext AI legal research platform, including its core legal research capabilities, document analysis tools, and AI-powered features such as CoCounsel, CARA (Case Analysis Research Assistant), Parallel Search, SmartCite, and Compose.

Casetext was founded in 2013 and acquired by Thomson Reuters in August 2023 for $650 million. The platform covers U.S. federal and state case law, statutes, regulations, and secondary legal sources. There is no public developer API; this schema is a conceptual model based on publicly documented platform capabilities.

## Schema Source

- Conceptual model derived from Casetext platform documentation and public product descriptions
- Platform URL: https://casetext.com
- CoCounsel: https://casetext.com/cocounsel/
- Parallel Search: https://casetext.com/parallel-search/

## Types Summary

| Category | Types |
|---|---|
| Case Law | Case, CaseDetails, CaseCitation, CaseType, CaseDocket, CaseStatus, CaseSummary |
| Courts | Court, CourtDetails, CourtLevel, CourtJurisdiction |
| Jurisdiction | Jurisdiction, JurisdictionDetails |
| Judges | Judge, JudgeDetails |
| Statutes | Statute, StatuteDetails, StatuteCode |
| Regulations | Regulation, RegulationDetails, CFR |
| Legislation | Bill, BillDetails, BillStatus |
| Citations | Citation, CitationDetails, CitationAnalysis, CitationTreatment, PrecedentStatus |
| Research | Research, ResearchQuery, SearchResults |
| Documents | Document, DocumentDetails |
| Briefs | Brief, BriefDetails |
| CARA AI | CARA, CARAAnalysis, Argument, ArgumentDetails, Similarity, SimilarCase |
| Memos | Memo, MemoDetails |
| Contracts | Contract, ContractAnalysis, ClauseAnalysis, RedlineComparison |
| API Access | APIKey, Token, RateLimitInfo |

## Query Capabilities

- `case(id: ID!)` - Retrieve a specific case by ID
- `searchCases(query: ResearchQuery!)` - Full-text and semantic search across case law
- `parallelSearch(query: String!, jurisdiction: String)` - Neural semantic search
- `statute(id: ID!)` - Retrieve a specific statute
- `regulation(id: ID!)` - Retrieve a specific regulation
- `citationAnalysis(citation: String!)` - SmartCite citator analysis
- `caraAnalysis(brief: String!)` - CARA brief analysis and similar case finding
- `researchMemo(query: String!)` - CoCounsel AI research memo generation

## Mutation Capabilities

- `createAPIKey(input: APIKeyInput!)` - Generate a new API key
- `uploadDocument(input: DocumentInput!)` - Upload a document for analysis
- `createBrief(input: BriefInput!)` - Submit a brief for CARA analysis
- `analyzContract(input: ContractInput!)` - Submit a contract for CoCounsel analysis
- `createMemo(input: MemoInput!)` - Request an AI-generated research memo

## Key Features Modeled

- **Parallel Search**: Neural semantic search engine for case law discovery
- **SmartCite**: Citator with precedent status signals and citation treatment tracking
- **CARA**: Case Analysis Research Assistant that identifies relevant cases from uploaded briefs
- **CoCounsel**: Generative AI assistant for document review, deposition prep, contract analysis, and research memos
- **AllSearch**: Private document search across firm-owned document collections
- **Compose**: Automated brief drafting

## Notes

- Casetext has no public API or SDK as of the acquisition by Thomson Reuters
- This schema is a conceptual representation for research and planning purposes
- The platform is sold as a SaaS subscription
- Post-acquisition, CoCounsel is integrated into Thomson Reuters Westlaw, Practical Law, and HighQ
