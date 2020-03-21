Jekyll::Hooks.register :posts, :pre_render do |post, payload|
  docExt = post.extname.tr('.', '')
  # only process if we deal with a markdown file
  if payload['site']['markdown_ext'].include? docExt
    newContent = post.content.gsub(/```mermaid([^`]+?)```/, '<div class="mermaid">\1</div>')
    post.content = newContent
  end
end
