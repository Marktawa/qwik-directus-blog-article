export default component$(() => {
  const article = useArticleLoader().value;
  const moreArticles = useMoreArticlesLoader().value;

  const navigate = useNavigate();
  const location = useLocation();
  const { id } = location.params;

  useVisibleTask$(() => {
    document.documentElement.scrollTo(0, 0);
  });

  if (!article) {
    return <NotFound />;
  }

  return (
    <div class="current-article">
      {article && (
        <section>
          <div class="container">
            <Link href="/" class="current-article__backlink">
              <IconBack className="icon" />
              <span>Back to Articles</span>
            </Link>
            <h1 class="current-article__title">{article.title}</h1>
            <div class="current-article__detail">
              <div class="current-article__wrapperOuter">
                <div class="current-article__wrapperInner">
                  <div class="current-article__authorImage">
                    <img
                      src={getAssetURL(article.author.avatar)}
                      alt=""
                      width="500"
                      height="500"
                      loading="lazy"
                    />
                  </div>
                  <div>
                    <div class="current-article__authorName">
                      {`${article.author.first_name} ${article.author.last_name}`}
                    </div>
                    <div class="current-article__time">
                      {article.publish_date}
                    </div>
                  </div>
                </div>
                <ul class="current-article__socials">
                  <li>
                    <a
                      href={`/articles/${article.id}`}
                      target="_blank"
                      rel="noreferrer noopener"
                    >
                      <IconLink />
                    </a>
                  </li>
                  <li>
                    <a
                      href="https://www.youtube.com/c/DirectusVideos"
                      target="_blank"
                      rel="noreferrer noopener"
                    >
                      <IconYoutube />
                    </a>
                  </li>
                  <li>
                    <a
                      href="https://www.linkedin.com/company/directus-io"
                      target="_blank"
                      rel="noreferrer noopener"
                    >
                      <IconLinkedin />
                    </a>
                  </li>
                  <li>
                    <a
                      href="https://twitter.com/directus"
                      target="_blank"
                      rel="noreferrer noopener"
                    >
                      <IconTwitter />
                    </a>
                  </li>
                </ul>
              </div>
              <div class="current-article_coverImage">
                <img src={getAssetURL(article.cover_image)} alt="" width="1920" height="1280" />
              </div>
            </div>
            <div class="current-article__body">
              <div
                class="current-article__bodyContent"
                dangerouslySetInnerHTML={article.body}
              ></div>
              <ul class="current-article__bodySocials">
                <li>
                  <a
                    href="https://github.com/directus"
                    target="_blank"
                    rel="noreferrer noopener"
                  >
                    <IconGithub />
                  </a>
                </li>
                <li>
                  <a
                    href="https://www.youtube.com/c/DirectusVideos"
                    target="_blank"
                    rel="noreferrer noopener"
                  >
                    <IconYoutube />
                  </a>
                </li>
                <li>
                  <a
                    href="https://www.linkedin.com/company/directus-io"
                    target="_blank"
                    rel="noreferrer noopener"
                  >
                    <IconLinkedin />
                  </a>
                </li>
                <li>
                  <a
                    href="https://twitter.com/directus"
                    target="_blank"
                    rel="noreferrer noopener"
                  >
                    <IconTwitter />
                  </a>
                </li>
              </ul>
            </div>
          </div>
        </section>
      )}

      {moreArticles && <MoreArticles articles={moreArticles} />}
    </div>
  );
});
