# JPA



객체그래프

1.(O)

-> 다른 연관관계를 참조할때 N+1 발생
	-> fetch join 활용
	
queryFactory

	.select(joinCompany)
		
	.from(joinCompany)
		
	.join(joinCompany.company, company).fetchJoin()
		
	.join(joinCompany.member, member).fetchJoin()
	   
        .where(joinCompany.member.id.eq(workerId)
		
		.and(joinCompany.accept.eq(accept)))
			
        .orderBy(company.name.asc())
	
	.fetch();

2.(X)

-> 다른 연관관계를 참조할때 N+1 발생

queryFactory

	.select(company) -> select는 company
		
	.from(joinCompany) -> from은 joinCompany
		
	.join(joinCompany.company, company).fetch join()
		
	.where(joinCompany.member.id.eq(workerId)
		
		.and(joinCompany.accept.eq(accept)))
			
	.orderBy(company.name.asc())
		
	.fetch();

	=>객체그래프가 맞지않음
		->fetch join을 사용하면 에러가남(1번예 사용해서 객체 그래프 탐색)




