# Architecture Decisions & Trade-offs

## Serverless (Lambda + S3)
Event-driven processing vs. always-on servers → 60% cost reduction, automatic scaling

## AWS Cognito Authentication  
Managed identity service vs. custom auth → SOC 2 compliance, 2-day implementation vs. weeks

## OpenAI Embeddings
Ada-002 vs. self-hosted models → $10/month vs. $1,000/month, 94% vs. 87% accuracy

## Pinecone Vector Database
Managed service vs. self-hosted → Sub-100ms queries, zero operational overhead

## Hybrid Text Processing
pdf-parse + Textract fallback → 60% cost savings vs. Textract-only, 94% success rate