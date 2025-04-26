# Requirements Specification

## Functional Requirements

1. **Scraping LinkedIn Saved Posts**: The system must scrape LinkedIn saved posts using the `LI_AT` cookie for authentication, ensuring that only the logged-in user's saved posts are accessed.
2. **Classification**: Each scraped post must be classified into predefined categories (e.g., GenAI, LLM, Data Engineering, etc.). If no category matches, the post should be marked as "Uncategorized."
3. **Storage**: Scraped and classified data must be stored in Supabase, leveraging `pgvector` for semantic search and `tsvector` for full-text search.
4. **APIs**: Provide Next.js Edge/serverless APIs for daily automated scraping (scheduled at 04:00 UTC) and manual "Sync Now" scraping.
5. **User Interface**: Implement a user interface using Tailwind CSS and shadcn-ui for displaying saved posts, filtering by categories, and initiating manual sync.
6. **Chat Interface**: Include a chat interface for users to interact with their saved posts, allowing multi-turn Q&A over the saved content.
7. **Authentication**: Ensure secure handling of the `LI_AT` cookie and other environment variables, with appropriate rotation and management.
8. **Logging and Analytics**: Implement logging and analytics to monitor usage, performance, and errors.

## Non-Functional Requirements

1. **Performance**: The system should provide a cold page load time of less than 600 ms (P95) for a dataset spanning 365 days.
2. **Cost Efficiency**: Daily LLM usage should not exceed $0.05.
3. **Security**: No sensitive information, such as API keys or cookies, should be leaked.
4. **Reliability**: The system should maintain high availability and handle errors gracefully.
5. **Scalability**: The architecture should support scaling to accommodate more data and users in future releases.
6. **Maintainability**: Code should adhere to best practices and be well-documented for ease of maintenance and future development.
7. **Usability**: The user interface should be intuitive and accessible, providing a seamless user experience.
8. **Compliance**: The system must comply with LinkedIn's terms of service and data privacy regulations.
9. **Observability**: Implement monitoring and logging to track system performance and usage metrics.

## Success Metrics

1. **Cold Page Load Time**: Achieve a cold page load time of less than 600 ms (P95) for a dataset spanning 365 days.
2. **Daily LLM Cost**: Maintain daily LLM usage costs at or below $0.05.
3. **Security**: Ensure zero leaked secrets or sensitive information.
4. **Lighthouse Performance Score**: Achieve a Lighthouse performance score of 90 or above.
5. **User Engagement**: Monitor user engagement metrics, such as the number of posts viewed, filtered, and interacted with via the chat interface.
6. **Error Rate**: Maintain a low error rate, with automated monitoring and alerts for any significant issues.

## Environment Details

- **Supabase**: The project will use Supabase for its backend, leveraging Postgres with `pgvector` and `tsvector` for vector and full-text search capabilities.
- **Next.js**: The frontend will be built using Next.js with the App Router for serverless API routes.
- **Tailwind CSS**: Tailwind CSS will be used for styling, along with shadcn-ui for UI components.
- **Vercel**: The application will be hosted on Vercel, utilizing its Edge Functions for serverless execution.
- **LLM**: The project will potentially use Gemini-2.5-flash for LLM tasks, with a context limit of 1 million tokens.
- **Environment Variables**: The following environment variables will be used and stored in a `.env.local` file:
  - `LI_AT`: LinkedIn session cookie
  - `OPENROUTER_API_KEY`: API key for OpenRouter
  - `FIRECRAWL_API_KEY`: API key for Firecrawl
  - `SUPABASE_URL`: Supabase project URL
  - `SUPABASE_ANON_KEY`: Supabase anonymous key

## Taxonomy

The project will use a predefined taxonomy for classifying LinkedIn posts. The taxonomy includes the following categories and subcategories:

| Topic   | Category             | Subcategory                  |
|---------|----------------------|------------------------------|
| GenAI   | Agents              | Frameworks / Tutorials       |
| LLM     | Fine-tuning/Quant.  | Tools (unsloth, vLLM)        |
| Data Eng| Vector DBs          | pgvector, qdrant, Chroma     |
| Dev Ops | Cloud               | AWS SageMaker, Bedrock       |
| Career  | Networking          | Interview Tips               |

If a post does not match any predefined category, it will be classified as "Uncategorized."