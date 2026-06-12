# Projeto-Senai

https://wcaquino.me/__/#/specs/runner?file=cypress/e2e/infantaria/infantaria.cy.js

/// <reference types="cypress" />

describe ('infantaria', () => {

    it ('visit', () => {
        cy.visit ('https://wcaquino.me/cypress/componentes.html')
        cy.get('#buttonSimple').click()
    })

    it.only('select', () => {
    cy.visit ('https://wcaquino.me/cypress/componentes.html')
        cy.get('[name="formNome"]').type('Weslley')
        cy.get('[data-cy="dataSobrenome"]').type('Ortiz')
        cy.get(':nth-child(1) > [name="formSexo"]').click()
        cy.get(':nth-child(2) > [name="formComidaFavorita"]').click()
        cy.get('[data-test="dataEscolaridade"]').select('Superior')
        cy.get('[data-testid="dataEsportes"]').select('Futebol')
        cy.get('[name="elementosForm:sugestoes"]').type('Escreve')
        cy.get(':nth-child(2) > :nth-child(1) > :nth-child(4) > input').click()
        cy.get(':nth-child(1) > :nth-child(5) > table > tbody > tr > td > input').click()
        cy.get('#tabelaUsuarios > :nth-child(2) > :nth-child(1) > :nth-child(6) > input').type('Escreva aqui')
        cy.get('[name="formCadastrar"]').click()
        cy.get('#resultado').should('be.visible').within(() => {
            cy.contains('Cadastrado!').should('be.visible')
            cy.get('#descNome').should('contain', 'Nome:').and('contain', 'Weslley')
            cy.get('#descSobrenome').should('contain', 'Sobrenome:').and('contain', 'Ortiz')
            cy.get('#descSexo').should('contain', 'Sexo:').and('contain', 'Masculino')
            cy.get('#descComida').should('contain', 'Comida:').and('contain', 'Frango')
            cy.get('#descEscolaridade').should('contain', 'Escolaridade:').and('contain', 'superior')
            cy.get('#descEsportes').should('contain', 'Esportes:').and('contain', 'Futebol')
            cy.get('#descSugestoes').should('contain', 'Sugestoes:').and('contain', 'Escreve')
        })
    })
})
