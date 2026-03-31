# Questions: analysis of routing behavior and failure modes

> **Q1**: What fraction of tokens are routed through each stage (I, II, III) across different datasets?

|               | Stage I → u | Stage II → g | Stage III → u | Stage III → p* |
| ------------- | ----------- | ------------ | ------------- | -------------- |
| Amazon-Review | 71.4%       | 12.7%        | 8.6%          | 7.3%           |
| LaMP-5        | 79.3%       | 13.4%        | 5.2%          | 2.1%           |
| PerGenBench   | 77.7%       | 16.4%        | 2.5%          | 3.4%           |

> **Q2**: In what cases does the constrained distribution p* (Eq. 8) fail to prevent factual errors?

We find that failures of the constrained distribution p* mainly arise when the feasible support set derived from the general model already contains incorrect candidates. In such cases, p* cannot fully prevent factual errors, as it relies on the general model to define the feasible region.

Additionally, when semantic alignment is overestimated (Stage III), the personalized model may introduce subtle semantic drift that is not fully filtered by Top-p truncation.



> **Q3**: Are there systematic patterns in routing errors (e.g., certain token types that are frequently misrouted)?

Misrouting errors are not uniformly distributed across tokens. They primarily occur at boundary tokens that exhibit mixed roles (e.g., tokens that are both stylistically expressive and semantically informative).

In contrast, strongly constrained factual tokens are rarely misrouted, indicating that Stage II (entropy-based constraint) effectively protects factual generation.

We will include additional analysis in the revision to further quantify these observations.
