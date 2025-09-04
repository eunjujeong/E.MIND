{% if directors.size > 0 %}
<h2>Director</h2>
<div class="people-grid">
  {% for person in directors %}
    <div class="person-card">
      <div class="person-content">
        {% if person.avatar %}
          <div class="person-avatar-container">
            <img src="{{ person.avatar | prepend: '/images/' | prepend: site.baseurl }}" alt="{{ person.title }}" class="person-avatar">
          </div>
        {% endif %}
        <div class="person-info">
          <h3><a href="{{ person.url | relative_url }}">{{ person.title }}</a></h3>
          {% if person.excerpt %}
            <p class="person-excerpt">{{ person.excerpt }}</p>
          {% endif %}
          {% if person.email %}
            <p class="person-email">
              <a href="mailto:{{ person.email }}">{{ person.email }}</a>
            </p>
          {% endif %}
        </div>
      </div>
    </div>
  {% endfor %}
</div>
{% endif %}

<style>
.people-grid {
  display: grid;
  grid-template-columns: repeat(auto-fit, minmax(400px, 1fr));  /* 카드 최소 너비 증가 */
  gap: 30px;
  margin: 20px 0 40px 0;
}

.person-card {
  border: 1px solid #ddd;
  border-radius: 8px;
  padding: 20px;
  transition: box-shadow 0.3s ease;
}

.person-card:hover {
  box-shadow: 0 4px 12px rgba(0,0,0,0.1);
}

.person-content {
  display: flex;
  align-items: flex-start;  /* 상단 정렬 */
  gap: 20px;  /* 사진과 텍스트 사이 간격 */
}

.person-avatar-container {
  flex-shrink: 0;  /* 사진 크기 고정 */
}

.person-avatar {
  width: 100px;
  height: 100px;
  border-radius: 50%;
  object-fit: cover;
}

.person-info {
  flex: 1;  /* 나머지 공간 모두 사용 */
  text-align: left;
}

.person-info h3 {
  margin: 0 0 10px 0;
}

.person-info h3 a {
  text-decoration: none;
  color: #333;
}

.person-info h3 a:hover {
  color: #0066cc;
}

.person-excerpt {
  color: #666;
  font-size: 0.9em;
  line-height: 1.4;
  margin: 10px 0;
}

.person-email {
  font-size: 0.9em;
  margin: 10px 0 0 0;
}

.person-email a {
  color: #0066cc;
  text-decoration: none;
}

@media (max-width: 768px) {
  .people-grid {
    grid-template-columns: 1fr;
  }
  
  .person-content {
    flex-direction: column;  /* 모바일에서는 세로 배치 */
    align-items: center;
    text-align: center;
  }
  
  .person-info {
    text-align: center;
  }
  
  .person-avatar {
    width: 80px;
    height: 80px;
  }
}
</style>
